---
title: "Need help with linux/C"
date: 2012-11-02
forum: General Help
---

### Post by iain150 on 2012-11-02
Hi this is my first post on the forums, I'm doing a course at university called C Programming Under Linux an I have gotten stuck on some of the questions and could use a bit of help.(Linux question after C)

Exercise 1
==========

Find the header file in which the value of PI is defined.
How many digits does the most precise PI implementation
have ?

Hints: Start by finding the C library glibc. There should
be a html-documentation of the C library somewhere. 
Have a look at what kind of standard functions there
are, make a qualified guess in which of the header files
PI might be defined and locate this file.


Exercise 2
==========

Is 2147483647 a prime number ?

Write a program that asks you to enter an integer number
and that prints 'Prime number' to the screen if the
number is a prime number and 'Not a Prime Number' if it
is not. The program may be simple, the algorithm does
not have to be smart, but it must use a function
int prime(int number) that returns 1 if the number is
a prime number and 0 if it is not. Use a properly
edited version of the provided 'Makefile' to compile
the program. Test the program with a couple of 
small numbers (e.g. 1 to 20), then get to the
question from the beginning:

So, is 2147483647 a prime number ?




On exercise 1 I used 

locate glibc
less /usr/share/man/man7/glibc.7.gz

within the file there was a link to [http://www.gnu.org/software/libc/documentation.html](http://www.gnu.org/software/libc/documentation.html) .
I followed this link and searched through it but it turned up a dead end, I have no subsequent ideas on how to complete this.

This is the supplied make file,

#-----------------------------------------------#
#    Makefile for unix systems                    #
#    using a GNU C compiler            #
#                                               #
#    adapt by replacing 'program' with          #
#    the name of your source code               #
#-----------------------------------------------#
CC=gcc
CFLAGS=-g -Wall -D__USE_FIXED_PROTOTYPES__ -ansi
#
# Compiler flags:
#    -g    -- Enable debugging
#    -Wall    -- Turn on all warnings
#    -D__USE_FIXED_PROTOTYPES__
#        -- Force the compiler to use the correct headers
#    -ansi    -- Don't use GNU extensions.  Stick to ANSI C.

high: high.c
    $(CC) $(CFLAGS) -o high high.c

clean:
    rm -f high 



This is my attempt at solving the problem,

/* Iain Taylor:  Prime number calculator*/
#include <stdio.h>
#include <stdlib.h>

float   test_number[10];
float   denom1;
int main() {
    (denom1=2.0);
    printf("Enter value to be tested.\n");
    scanf(test_number, sizeof(test_number), stdin);
    sscanf("%d", &test_number);
while (1) 
    (denom1<=test_number);/* stop once test_number and the denomonator are equal */
{   
    while (0) {
        (test_number/denom1==%d);/* While test_number/denom1 is not an intiger increment the denomonator (denom1) */
        denom1++;
        printf("%d is a prime number.\n",denom1);
    else
        printf("%d \n",test_number);
    }
}

I end up with a lot of bugs and i can't figure out how to fix them.

Linux question,

Write a script which checks for a .bak (backup) file for every .data file in the current
directory (i.e. for every xxx.data file there should also be a xxx.data.bak file).
Your script should report if there is a missing .bak and create one. Run your script in the
data directory to check it works.

This is my attempt,

#!/bin/bash

A=*.data
B=$A.bak

for $A in *
  do 
if
[ -e $A ]; then
[ -e $B ];
  else 
    echo "$B missing creating now"
    touch $B
fi
done
exit

Inevitably someone is going to say do your own homework, this is outwith my understanding of the course and I need help to progress.
I have to go to my lectures now but i will be back at 1pm GMT.

---

### Post by dino99 on 2012-11-02
i really know nothing about C, but googling i know :P

[https://www.gnu.org/software/libc/manual/html_node/Mathematical-Constants.html](https://www.gnu.org/software/libc/manual/html_node/Mathematical-Constants.html)

thats for question 1 :P

you surely can find the others too following my rule :) ( you're not the first student fighting with such question)

---

### Post by rnerwein on 2012-11-02
> **iain150 said:**
> Hi this is my first post on the forums, I'm doing a course at university called C Programming Under Linux an I have gotten stuck on some of the questions and could use a bit of help.(Linux question after C)

Exercise 1
==========

Find the header file in which the value of PI is defined.
How many digits does the most precise PI implementation
have ?

Hints: Start by finding the C library glibc. There should
be a html-documentation of the C library somewhere. 
Have a look at what kind of standard functions there
are, make a qualified guess in which of the header files
PI might be defined and locate this file.


Exercise 2
==========

Is 2147483647 a prime number ?

Write a program that asks you to enter an integer number
and that prints 'Prime number' to the screen if the
number is a prime number and 'Not a Prime Number' if it
is not. The program may be simple, the algorithm does
not have to be smart, but it must use a function
int prime(int number) that returns 1 if the number is
a prime number and 0 if it is not. Use a properly
edited version of the provided 'Makefile' to compile
the program. Test the program with a couple of 
small numbers (e.g. 1 to 20), then get to the
question from the beginning:

So, is 2147483647 a prime number ?




On exercise 1 I used 

locate glibc
less /usr/share/man/man7/glibc.7.gz

within the file there was a link to [http://www.gnu.org/software/libc/documentation.html](http://www.gnu.org/software/libc/documentation.html) .
I followed this link and searched through it but it turned up a dead end, I have no subsequent ideas on how to complete this.

This is the supplied make file,

#-----------------------------------------------#
#    Makefile for unix systems                    #
#    using a GNU C compiler            #
#                                               #
#    adapt by replacing 'program' with          #
#    the name of your source code               #
#-----------------------------------------------#
CC=gcc
CFLAGS=-g -Wall -D__USE_FIXED_PROTOTYPES__ -ansi
#
# Compiler flags:
#    -g    -- Enable debugging
#    -Wall    -- Turn on all warnings
#    -D__USE_FIXED_PROTOTYPES__
#        -- Force the compiler to use the correct headers
#    -ansi    -- Don't use GNU extensions.  Stick to ANSI C.

high: high.c
    $(CC) $(CFLAGS) -o high high.c

clean:
    rm -f high 



This is my attempt at solving the problem,

/* Iain Taylor:  Prime number calculator*/
#include <stdio.h>
#include <stdlib.h>

float   test_number[10];
float   denom1;
int main() {
    (denom1=2.0);
    printf("Enter value to be tested.\n");
    scanf(test_number, sizeof(test_number), stdin);
    sscanf("%d", &test_number);
while (1) 
    (denom1<=test_number);/* stop once test_number and the denomonator are equal */
{   
    while (0) {
        (test_number/denom1==%d);/* While test_number/denom1 is not an intiger increment the denomonator (denom1) */
        denom1++;
        printf("%d is a prime number.\n",denom1);
    else
        printf("%d \n",test_number);
    }
}

I end up with a lot of bugs and i can't figure out how to fix them.

Linux question,

Write a script which checks for a .bak (backup) file for every .data file in the current
directory (i.e. for every xxx.data file there should also be a xxx.data.bak file).
Your script should report if there is a missing .bak and create one. Run your script in the
data directory to check it works.

This is my attempt,

#!/bin/bash

A=*.data
B=$A.bak

for $A in *
  do 
if
[ -e $A ]; then
[ -e $B ];
  else 
    echo "$B missing creating now"
    touch $B
fi
done
exit

Inevitably someone is going to say do your own homework, this is outwith my understanding of the course and I need help to progress.
I have to go to my lectures now but i will be back at 1pm GMT.

hi
for exercise 1 i will use:
[COLOR=Blue]cd /usr/include
grep -inH ' PI ' `find . -name "*.h" -type f`[/COLOR]
here is the output of my find command:
./ncursesw/curses.h:291:#define ACS_PI        NCURSES_ACS('{') /* Pi */
./ncursesw/curses.h:1541:#define WACS_PI        NCURSES_WACS('{') /* Pi */
./math.h:367:# define M_PI        3.14159265358979323846    /* pi */
./math.h:386:# define M_PIl        3.1415926535897932384626433832795029L  /* pi */
./linux/ixjuser.h:157:* freq = cos(2 * PI * frequency / 8000)
./curses.h:291:#define ACS_PI        NCURSES_ACS('{') /* Pi */
root@tschang:/usr/include 15:01-> cd /usr/include
root@tschang:/usr/include 15:08-> grep -inH ' PI ' `find . -name "*.h" -type f`
./ncursesw/curses.h:291:#define ACS_PI        NCURSES_ACS('{') /* Pi */
./ncursesw/curses.h:1541:#define WACS_PI        NCURSES_WACS('{') /* Pi */
./math.h:367:# define M_PI        3.14159265358979323846    /* pi */
./math.h:386:# define M_PIl        3.1415926535897932384626433832795029L  /* pi */
./linux/ixjuser.h:157:* freq = cos(2 * PI * frequency / 8000)
./curses.h:291:#define ACS_PI        NCURSES_ACS('{') /* Pi */
root@tschang:/usr/include 15:08-> 

you can see - PI is defined in math.h line 386 line 387

i hope it helps a little bi
tschau
   richi

---

### Post by codemaniac on 2012-11-02
By the way,this might not be the right forum to paste home works. ;)

---

### Post by Mark Phelps on 2012-11-02
We are not a homework service. Please see code of conduct which you agreed to.

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

> 
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued

---

### Post by Elfy on 2012-11-03
Closed.

---

