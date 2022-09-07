## Problem 1: Regular Expressions

1.

letter ::= [A-Z] | [a-z] | _
digit ::= [0-9]

c_ident ::= letter (letter | digit)*

2.

digit ::= [0-9]
fdigit ::= [2-9]

tdigit ::= fdigit digit digit 
area ::= '(' tdigit ')' | tdigit
central ::= tdigit
subscriber ::= digit digit digit digit

number ::= area '.' central '.' subscriber | area - central - subscriber

3.

tdigit ::= [0-3]
odigit ::= [0-7]
octal ::= (odigit)? odigit | tdigit odigit odigit

hdigit ::= [0-9] | [a-f] | [A-F]
nzhdigit ::= [1-9] | [a-f] | [A-F]
nfzhdigit ::= [1-9] | [a-e] | [A-E]
nfhdigit ::= [0-9] | [a-e] | [A-E]
nahdigit ::= [0-9] | [b-f] | [B-F]

unicode ::= u (nzhdigit hdigit hdigit hdigit |
               0 (nzhdigit hdigit hdigit |
                  0 (nfzhdigit hdigit |
                     0 nahdigit |
                     (f | F) nfhdigit)))


escape ::= \ (b | t | n | f | r | ''' | " | \ | octal | unicode)

string ::= "([^", \, '\n', '\r'] | escape)*"

## Problem 2: Context-Free Grammars

### Part 1

A. The grammar describes all words over alphabet {a,b} that contain
more occurrences of b than a.

B.
                  S
                 / \
                M   B
               /   / \
              S   b   C
             / \      |
            M   B_    epsilon
            |   | \
      epsilon   b  C
                  / \
                 b   A
                    / \
                   a   C
                       |
                       epsilon


### Part 2

           E
          /|\_
         / O  \
        N  |   E
        |  +  /|\_
        3    / O  \
            /  |   E
            E  /  /|\_
           /|\   E O  \
          N * N  | |   E
          |   |  N ** /|\
          5   6  |   E O E
                 8   | |  \
                     2 **  N
                           |
                           2
