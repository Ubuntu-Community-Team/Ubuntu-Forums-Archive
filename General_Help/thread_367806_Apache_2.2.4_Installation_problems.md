---
title: "Apache 2.2.4 Installation problems"
date: 2007-02-22
forum: General Help
---

### Post by James- on 2007-02-22
well I'm trying to install apache-2.2.4 from the documentation available [here]("http://httpd.apache.org/docs/2.2/install.html")

I'm using UBUNTU-SERVER and have installed the fallowing things:
> 
aptitude install gcc libc6-dev
apt-get install make
sudo apt-get install build-essential


when I try to configure for the executable with this command:
> 
$ CC="pgcc" CFLAGS="-O2" \./configure --prefix=/sw/pkg/apache \--enable-rewrite=shared \--enable-speling=shared


I get the fallowing error:
> 
checking for C compiler default output file name... configure: error: 
C compiler cannot create executables

Would appreciate the help ^_^

---

### Post by sardion on 2007-02-22
Why are you trying to use pgcc for the compiler?

Do you have pgcc installed correctly?

---

### Post by James- on 2007-02-22
i didn't actually know what the command was x_X first time using this(trying to learn)

---

### Post by sardion on 2007-02-22
Change your command line to use CC="gcc" instead of pgcc.  Then it should work.

gcc is the standard c compiler (the CC= tells what compiler to use).  pgcc is different.

You can also just drop the CC="" part from the command entirely.

---

### Post by James- on 2007-02-22
and what do the CFLAGS do? kinda like the write permissions? or what? p.s. thanks for the help :D

---

### Post by sardion on 2007-02-22
CFLAGS are flags passed to the compiler on the command line

if you look at 

man gcc

you will see that it is a command line program.  CFLAGS="..." passes ... to gcc when it is called.

The -O2 flag tells it to optimize the code for speed.


I would say look at man gcc
and do some google searches for "gcc documentation" or "gcc howto" to learn more.


Myself, I learned by just compiling a lot of stuff from source (you can always download and compile from source even if the stuff is in the repos, just don't try to install it).  Learn by doing is how I treat linux.

---

### Post by James- on 2007-02-22
well thanks a lot for your help, that's why I'm trying to learn :P cause I suck at Linux.. guess COBOL skills don't translate :P

---

