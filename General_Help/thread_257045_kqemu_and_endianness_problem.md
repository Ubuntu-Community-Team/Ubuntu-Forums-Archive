---
title: "kqemu and endianness problem"
date: 2006-09-14
forum: General Help
---

### Post by Tibor60 on 2006-09-14
I installed qemu and all is ok, but very-very slow. I tried ti install kqemu to speed up, but receive the error message when compiling:

tibor@GOLDEN10:~$ cd /tmp/kqemu-1.3.0pre9/
tibor@GOLDEN10:/tmp/kqemu-1.3.0pre9$ ./configure
big/little test failed
Source path       /tmp/kqemu-1.3.0pre9
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386

kernel sources    /usr/src/linux
kbuild type       2.6
tibor@GOLDEN10:/tmp/kqemu-1.3.0pre9$

what to do with this big/little test not to fail???
Please help, I have no the slightest idea what to do...

---

### Post by croto on 2006-12-03
try installing build-essentials first

---

