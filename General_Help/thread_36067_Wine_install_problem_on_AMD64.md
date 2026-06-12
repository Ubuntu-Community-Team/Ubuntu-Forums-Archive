---
title: "Wine install problem on AMD64"
date: 2005-05-21
forum: General Help
---

### Post by hammett111 on 2005-05-21
Okay Peeps heres my Problem

I followed this manual install How to do for Wine [http://www.ubuntuforums.org/showthread.php?t=29996&highlight=wine+amd64](http://www.ubuntuforums.org/showthread.php?t=29996&highlight=wine+amd64)

Unfrtunately after I enter the ./tools/wineinstall commmand I get the following Bollocks!!!!

quentin@ubuntu:~/cvs/wine$ ./tools/wineinstall
WINE Installer v0.74

Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.
quentin@ubuntu:~/cvs/wine$

HELP!!!!!!!

---

### Post by ::DoGG:: on 2005-05-31
Update binutils to the newest version , that helped me.

---

### Post by hammett111 on 2005-06-12
I just put CC=gcc before the ./configure, so all good. New Probs arose though in the form of this after make, any clues, I used gcc-4.0 to compile!!

quentin@ubuntu:~/cvs/wine$ sudo make
Password:
make[1]: Entering directory `/home/quentin/cvs/wine/libs'
make[2]: Entering directory `/home/quentin/cvs/wine/libs/port'
gcc-4.0 -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -gstabs+ -Wpointer-arith  -g -O2 -D__i386__ -o interlocked.o interlocked.c
{standard input}: Assembler messages:
{standard input}:214: Error: `12(%esp)' is not a valid 64 bit base/index expression
{standard input}:215: Error: `8(%esp)' is not a valid 64 bit base/index expression
{standard input}:216: Error: `4(%esp)' is not a valid 64 bit base/index expression

---

### Post by Natja on 2005-07-24
Same problem for me  :???:

---

