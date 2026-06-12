---
title: "gmake not working"
date: 2007-08-28
forum: General Help
---

### Post by ThePhilosopher on 2007-08-28
Im trying to compiling a program.
In the readme file it says to type gmake to compile but i get this error:

trebbi@trebbi-desktop:~/Programmi/spruce-0.2$ gmake
gcc -g -Wall -Werror -O2  -c spruce_snd.c
cc1: warnings being treated as errors
spruce_snd.c: In function &#8216;control_connect&#8217;:
spruce_snd.c:347: warning: pointer targets in passing argument 5 of &#8216;getsockopt&#8217; differ in signedness
gmake: *** [spruce_snd.o] Error 1
trebbi@trebbi-desktop:~/Programmi/spruce-0.2$                    

i ve done the apt-get install build-essential.

How can i fix it?

Thx anyway

---

### Post by ThePhilosopher on 2007-08-28
Im trying to compiling a program.
 In the readme file it says to type gmake to compile but i get this error:
 
 trebbi@trebbi-desktop:~/Programmi/spruce-0.2$ gmake
 gcc -g -Wall -Werror -O2 -c spruce_snd.c
 cc1: warnings being treated as errors
 spruce_snd.c: In function &#8216;control_connect&#8217;:
 spruce_snd.c:347: warning: pointer targets in passing argument 5 of &#8216;getsockopt&#8217; differ in signedness
 gmake: *** [spruce_snd.o] Error 1
 trebbi@trebbi-desktop:~/Programmi/spruce-0.2$ 
 
 i ve done the apt-get install build-essential.
 
 How can i fix it?
 
 Thx anyway

---

### Post by K.Mandla on 2007-08-28
Merged identical threads. ;) 

There might be a command line flag (or maybe a configure flag) that doesn't mark warnings as errors. It seems to be stopping at a warning, and that might push it on through without stopping. I don't know enough about gmake to know if there are flags like that though. :|

---

