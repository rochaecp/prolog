# Prolog

## Anotações 

- Prolog não é tipada - não tem tipos - tudo é termo
- Prolog possui termos
  - Termos simples
    - átomos: ctes num e alfanumericas
    - variáveis: X
  - Termos funcionais (cláusulas)
    - fatos/consultas
    - regras de inferencia

## Comentários

- Usamos %

## Operadores lógicos

- , And
- ; Or
- = Unificação
- \= Negação da unificação
- == Teste de identidade
- \== Negação da identidade
- =:= Igualdade aritmética
- < > >= =< Operadores relacionais
- := Condicional

## Operadores aritméticos

- +   Soma
- -   Subtração
- *   Multiplicação
- /   Divisão
- //  parte inteira da divisão (ou div)
- mod Resto da divisão inteira
- ^   Potência

## Algumas funções úteis

- abs(X) Valor absoluto de X
- cos(X) Cosseno de X
- exp(x) Valor de "e" elevado a X
- ln(X) Logaritmo natural de X
- log(X) Logaritmo decimal de X
- sin(X) Seno de X
- sqrt(X) Raiz quadrada de X
- tan(x) Tangente de X
- round(X) Arredonda X para N casas decimais
- random Um número aleatório entre 0 e 1


## Recursividade

~~~prolog
% programa do fatorial
fatorial(0, 1):-!. % criterio de parada
fatorial(N, X):-N1 is N-1, fatorial(N1,X1), X is N*X1. % uso da recursao

% query para testar programa
fatorial(5,X).
~~~

## Listas

Exemplos:
  - Mais em: <https://pt.wikibooks.org/wiki/Prolog/Exemplos>

~~~prolog
[] % lista vazia
[mauricio, maria, jose] % lista simples
[[amor, felicidade], [paz, alegria]]% lista de listas

% separando a cabeça
[H|T] = [1,2,3]. % H é 1 e T é [2, 3] - o | delimita a cauda da lista

% somando elementos da lista
soma([],0).
soma([H|T],S):-soma(T,G),S is H+G.

% tam de uma lista
tamL([_], 1):- !.
tamL([_|L], T):- tamL(L, X), T is X + 1.

% imprimir cada elemento da lista
printList([]).
printList([X|List]) :-
	write(X),nl,
    printList(List).

% ultimo elemento da lista
last([X], X).
last([_|Xs],X):- last(Xs, X). % testa com last([1, 2, 3, 8, 10], W)

% invertendo lista
inverteLst([],[]).  
inverteLst([X], [X]).
inverteLst( [X|Xs] , R ) :- 
  inverteLst(Xs,T), append( T , [X] , R ).

~~~

### Associações de valores

X is 10, Q is X*2, write(Q). % retorna 20

inc(X,Resultado) :- Resultado is X+1. % inc(2,Resultado).
dec(X,Resultado) :- Resultado is X-1.

## Exemplos

- termos em letra maiúscula são variáveis
- exemplo
  - homem(socrates)
  - mortal(X):-homem(X)
  - ?mortal(socrates)
  - yes

## Links

- interpretador online: <https://swish.swi-prolog.org/>

% questao 1
aconselha('Spock', 'Kirk').
aconselha('Diana', 'Picard').
comanda('Archer', 'NX-01').
comanda('Kirk', 'NCC-1701'). 
comanda('Picard', 'NCC-1701-D').
comanda('Janeway', 'Voyager').
comanda('Almak', 'IRW TMet').
eh_um('IRW TMet', 'D-deridex').
eh_um('D-deridex', 'Nave').
eh_um('NX-01', 'Enterprise').
eh_um('NCC-1701', 'Enterprise').
eh_um('NCC-1701-D', 'Enterprise').
eh_um('Voyager', 'Enterprise').
eh_um('Enterprise', 'Nave').
pertence('D-deridex', 'Imperio Romulano').
pertence('Enterprise', 'Federação').
locomocao('Enterprise', 'Motor de dobra').

% questao 2
comandante(X, Y) :- comanda(X, Z), eh_um(Z, W), pertence(W, Y);
    comanda(X, Z), eh_um(Z, W), locomocao(W, Y);
    comanda(X, Z), eh_um(Z, W), eh_um(W, Y).

% questao 3
inimigos(X1, X2) :- comanda(X1, Z1), eh_um(Z1, W1), pertence(W1, F1), 
    comanda(X2, Z2), eh_um(Z2, W2), pertence(W2, F2),
    F1 \== F2.

% questao 4

    












