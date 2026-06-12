---
title: "trying to install open2300"
date: 2008-05-31
forum: General Help
---

### Post by Paul VW on 2008-05-31
Open 2300 is a program for using your weather station on Linux [http://www.lavrsen.dk/twiki/bin/view/Open2300/WebHome](http://www.lavrsen.dk/twiki/bin/view/Open2300/WebHome)

I am running Hardy Heron with all the updates, I downloaded the .tar.gz file and unpaked it, but in terminal when I type make I get this message

paul@paul-desktop:~/open$ make
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o open2300.o open2300.c
In file included from rw2300.h:15,
                 from open2300.c:11:
linux2300.h:7:21: error: termios.h: No such file or directory
linux2300.h:8:20: error: unistd.h: No such file or directory
linux2300.h:9:24: error: netinet/in.h: No such file or directory
linux2300.h:10:24: error: arpa/inet.h: No such file or directory
linux2300.h:11:23: error: sys/ioctl.h: No such file or directory
linux2300.h:12:24: error: sys/socket.h: No such file or directory
linux2300.h:13:19: error: netdb.h: No such file or directory
In file included from open2300.c:11:
rw2300.h:18:20: error: string.h: No such file or directory
rw2300.h:19:19: error: fcntl.h: No such file or directory
rw2300.h:20:19: error: stdio.h: No such file or directory
rw2300.h:21:18: error: time.h: No such file or directory
rw2300.h:22:20: error: stdlib.h: No such file or directory
rw2300.h:24:18: error: math.h: No such file or directory
rw2300.h:25:23: error: sys/types.h: No such file or directory
rw2300.h:26:22: error: sys/stat.h: No such file or directory
open2300.c: In function ‘print_usage’:
open2300.c:27: warning: implicit declaration of function ‘printf’
open2300.c:27: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:36: warning: implicit declaration of function ‘exit’
open2300.c:36: warning: incompatible implicit declaration of built-in function ‘exit’
open2300.c: In function ‘main’:
open2300.c:81: warning: incompatible implicit declaration of built-in function ‘exit’
open2300.c:84: warning: implicit declaration of function ‘strcmp’
open2300.c:87: warning: implicit declaration of function ‘atoi’
open2300.c:91: warning: implicit declaration of function ‘strlen’
open2300.c:91: warning: incompatible implicit declaration of built-in function ‘strlen’
open2300.c:95: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:96: warning: incompatible implicit declaration of built-in function ‘exit’
open2300.c:103: warning: implicit declaration of function ‘strtol’
open2300.c:103: error: ‘NULL’ undeclared (first use in this function)
open2300.c:103: error: (Each undeclared identifier is reported only once
open2300.c:103: error: for each function it appears in.)
open2300.c:111: warning: incompatible implicit declaration of built-in function ‘strlen’
open2300.c:115: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:116: warning: incompatible implicit declaration of built-in function ‘exit’
open2300.c:123: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:124: warning: incompatible implicit declaration of built-in function ‘exit’
open2300.c:143: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:144: warning: incompatible implicit declaration of built-in function ‘exit’
open2300.c:173: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:174: warning: incompatible implicit declaration of built-in function ‘exit’
open2300.c:178: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:203: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:204: warning: incompatible implicit declaration of built-in function ‘exit’
open2300.c:208: warning: incompatible implicit declaration of built-in function ‘printf’
open2300.c:226: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [open2300.o] Error 1


anyideas?

Thanks :)

---

### Post by Paul VW on 2008-05-31
*cough cough*

---

### Post by bwhite82 on 2008-05-31
First, make sure you have the package: build-essential installed. Then, open up INSTALL in the tar.gz you downloaded which contain detailed instructions.

---

### Post by shifty_powers on 2008-05-31
have you used configure before make?

---

### Post by bwhite82 on 2008-05-31
> **shifty_powers said:**
> have you used configure before make?

I didn't see a configure script in the archive.

---

### Post by Paul VW on 2008-06-01
urmm, I tried to run the install file first, but that did not work (nothing happened at all) 

I dont understand what you mean by "the package build-essential" installed, I cant see it on the list of programs installed.

I am a bit of a novice at installing programs, I have always used the add/remove feature before.

---

### Post by Paul VW on 2008-06-01
urmmm? anyone?

---

### Post by shifty_powers on 2008-06-01
```
sudo apt-get install build-essential
``` 
into a terminal ;)

it's a series of libs and such like that are vital to any compiling :D

---

### Post by shifty_powers on 2008-06-01
also, try ```
sudo make
```

---

### Post by Paul VW on 2008-06-01
well the build essential worked :)

but when I typed sudo make I got this

```
paul@paul-desktop:~$ sudo make
make: *** No targets specified and no makefile found. Stop.
paul@paul-desktop:~$ cd open
paul@paul-desktop:~/open$ sudo make
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o open2300.o open2300.c
open2300.c: In function ‘main’:
open2300.c:103: warning: pointer targets in passing argument 1 of ‘strtol’ differ in signedness
open2300.c:127: warning: pointer targets in passing argument 1 of ‘strtol’ differ in signedness
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o rw2300.o rw2300.c
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o linux2300.o linux2300.c
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o win2300.o win2300.c
gcc -Wall -O3 -DVERSION=\"1.10\" -o open2300 open2300.o rw2300.o linux2300.o win2300.o -lm
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o dump2300.o dump2300.c
gcc -Wall -O3 -DVERSION=\"1.10\" -o dump2300 dump2300.o rw2300.o linux2300.o win2300.o -lm
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o log2300.o log2300.c
log2300.c: In function ‘main’:
log2300.c:89: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:95: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:101: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:106: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:111: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:117: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:118: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:124: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:130: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:136: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:142: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:148: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
log2300.c:154: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
gcc -Wall -O3 -DVERSION=\"1.10\" -o log2300 log2300.o rw2300.o linux2300.o win2300.o -lm 
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o fetch2300.o fetch2300.c
fetch2300.c: In function ‘main’:
fetch2300.c:50: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:55: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:56: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:59: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:62: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:68: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:73: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:74: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:77: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:80: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:86: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:91: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:92: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:95: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:98: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:105: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:107: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:108: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:111: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:114: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:121: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:123: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:124: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:127: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:130: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:136: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:140: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:146: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:151: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:152: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:156: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:159: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:167: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:168: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:172: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:175: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:182: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:183: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:186: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:193: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:194: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:197: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:203: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:206: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:212: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:220: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:221: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:225: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:228: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
fetch2300.c:234: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
gcc -Wall -O3 -DVERSION=\"1.10\" -o fetch2300 fetch2300.o rw2300.o linux2300.o win2300.o -lm
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o wu2300.o wu2300.c
wu2300.c: In function ‘main’:
wu2300.c:43: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:51: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:57: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:62: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:67: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:73: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:74: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:79: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:84: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:90: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:95: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
wu2300.c:109: warning: pointer targets in passing argument 1 of ‘http_request_url’ differ in signedness
gcc -Wall -O3 -DVERSION=\"1.10\" -o wu2300 wu2300.o rw2300.o linux2300.o win2300.o -lm 
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o cw2300.o cw2300.c
cw2300.c: In function ‘main’:
cw2300.c:64: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:69: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:70: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:79: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:82: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:85: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:91: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:94: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:97: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
cw2300.c:103: warning: pointer targets in passing argument 2 of ‘citizen_weather_send’ differ in signedness
gcc -Wall -O3 -DVERSION=\"1.10\" -o cw2300 cw2300.o rw2300.o linux2300.o win2300.o -lm 
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o history2300.o history2300.c
gcc -Wall -O3 -DVERSION=\"1.10\" -o history2300 history2300.o rw2300.o linux2300.o win2300.o -lm
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o histlog2300.o histlog2300.c
histlog2300.c: In function ‘main’:
histlog2300.c:177: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
histlog2300.c:181: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:186: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:191: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:196: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:201: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:206: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:207: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:212: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:230: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
histlog2300.c:234: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
gcc -Wall -O3 -DVERSION=\"1.10\" -o histlog2300 histlog2300.o rw2300.o linux2300.o win2300.o -lm 
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o bin2300.o bin2300.c
gcc -Wall -O3 -DVERSION=\"1.10\" -o bin2300 bin2300.o rw2300.o linux2300.o win2300.o -lm
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o xml2300.o xml2300.c
gcc -Wall -O3 -DVERSION=\"1.10\" -o xml2300 xml2300.o rw2300.o linux2300.o win2300.o -lm 
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o light2300.o light2300.c
gcc -Wall -O3 -DVERSION=\"1.10\" -o light2300 light2300.o rw2300.o linux2300.o win2300.o -lm
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o interval2300.o interval2300.c
gcc -Wall -O3 -DVERSION=\"1.10\" -o interval2300 interval2300.o rw2300.o linux2300.o win2300.o -lm
gcc -Wall -O3 -DVERSION=\"1.10\"   -c -o minmax2300.o minmax2300.c
gcc -Wall -O3 -DVERSION=\"1.10\" -o minmax2300 minmax2300.o rw2300.o linux2300.o win2300.o -lm 

```

I have a feeling thats not good? :confused::confused:

---

### Post by shifty_powers on 2008-06-01
heh, what happens with just make then? (i.e. no sudo)

---

### Post by shifty_powers on 2008-06-01
and does it stop there?

---

### Post by shifty_powers on 2008-06-01
having just looked at it, there is no configure script, and it mentions the possibility of editing the make file.

this may be beyond my abilities dude ;)

---

### Post by loridant on 2009-01-25
Hello
I have the same pb ! Have you find a solution ?
Regards
Fred (France)

---

### Post by loridant on 2009-01-26
It's OK now. The problem comes form GCC. You must use GCC-3.3 (and under Festy and later, it's GCC-4.2.

- apt-get install gcc-3.3
and after :
root@fit-PC:/#rd /usr/bin/gcc
root@fit-PC:/# ln -s /usr/bin/gcc-3.3 /usr/bin/gcc
root@fit-PC:/# gcc -v
Lecture des spécification à partir de /usr/lib/gcc-lib/i486-linux-gnu/3.3.6/specs
Configuré avec: ../src/configure -v --enable-languages=c,c++ --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --enable-__cxa_atexit --with-system-zlib --enable-nls --without-included-gettext --enable-clocale=gnu --enable-debug i486-linux-gnu
Modèle de thread: posix
version gcc 3.3.6 (Ubuntu 1:3.3.6-15ubuntu2)

and after, NO PROBLEM
my weather station : [www.photorock.com/meteo](www.photorock.com/meteo)
FRED

---

