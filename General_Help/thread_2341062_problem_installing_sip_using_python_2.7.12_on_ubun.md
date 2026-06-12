---
title: "problem installing sip using python 2.7.12 on ubuntu 16.04"
date: 2016-10-24
forum: General Help
---

### Post by guzbandu on 2016-10-24
we downloaded sip 4.18.1 and followed the README

python configure.py
make

on running make we received the following error message:

make[1]: Entering directory '/home/jennifer/Downloads/sip-4.18.1/sipgen'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/jennifer/Downloads/sip-4.18.1/sipgen'
make[1]: Entering directory '/home/jennifer/Downloads/sip-4.18.1/siplib'
gcc -c -pipe -fPIC -O2 -Wall -W -DNDEBUG -I. -I/usr/include/python2.7 -o siplib.o siplib.c
siplib.c:20:20: fatal error: Python.h: No such file or directory
compilation terminated.
Makefile:29: recipe for target 'siplib.o' failed
make[1]: *** [siplib.o] Error 1
make[1]: Leaving directory '/home/jennifer/Downloads/sip-4.18.1/siplib'
Makefile:3: recipe for target 'all' failed
make: *** [all] Error 2

---

### Post by steeldriver on 2016-10-24
Hello and welcome to the forums

Did you install the libpython-dev package?

BTW python-sip 4.17 should be available from the 16.04 'universe' repository

---

### Post by guzbandu on 2016-10-24
python-sip 4.1.7 is not available from my 'universe' repository, however, I did manage to install the libpython-dev package using apt-get and that solved my problem.

Thank you.

---

