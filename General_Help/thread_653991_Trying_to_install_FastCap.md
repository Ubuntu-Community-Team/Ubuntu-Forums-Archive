---
title: "Trying to install FastCap"
date: 2007-12-30
forum: General Help
---

### Post by JunsuinoKokoro on 2007-12-30
I am trying to install a program called FastCap.  The readme file tells me that I should be typing in the command 'make all' to compile and create the executables.  Here's what happens:

brien@BRIENBLIATOU-PC:~/Programs/FastCap2.0-18Sep92$ ls
bin  config  doc  examples  Makefile  README  src
brien@BRIENBLIATOU-PC:~/Programs/FastCap2.0-18Sep92$ make all
make[1]: Entering directory `/home/brien/Programs/FastCap2.0-18Sep92/src'
make[1]: Leaving directory `/home/brien/Programs/FastCap2.0-18Sep92/src'
cd src ; make fastcap
make[1]: Entering directory `/home/brien/Programs/FastCap2.0-18Sep92/src'
cc -O -DOTHER   -c -o mulGlobal.o mulGlobal.c
In file included from mulGlobal.c:36:
mulGlobal.h:46:20: error: malloc.h: No such file or directory
mulGlobal.h:48:19: error: stdio.h: No such file or directory
mulGlobal.h:49:18: error: math.h: No such file or directory
mulGlobal.h:60:18: error: time.h: No such file or directory
mulGlobal.c:69: error: ‘NULL’ undeclared here (not in a function)
make[1]: *** [mulGlobal.o] Error 1
make[1]: Leaving directory `/home/brien/Programs/FastCap2.0-18Sep92/src'
make: *** [fastcap] Error 2
brien@BRIENBLIATOU-PC:~/Programs/FastCap2.0-18Sep92$ 


Now it's been a long time since I've programmed in C, and it's my first time using Linux, but it would seem to me that I'm not able to compile the program because some things are missing from the C standard library.  If anyone can help me figure out how to compile this, I'd really appreciate it.  Thank you.

---

