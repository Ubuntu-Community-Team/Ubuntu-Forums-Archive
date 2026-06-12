---
title: "g++ error"
date: 2007-06-11
forum: General Help
---

### Post by Biglia on 2007-06-11
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstdlib:135: error: ‘::system’ has not been declared

when i try to compile a program with g++ it always return this error in the shell... can someone help me??

---

### Post by iThink on 2007-06-14
This error also had happened to me,and i figured it out .
I just commented "#undef system" in cstdlib.h in /usr/inlcude/c++/4.1.2,
then it works.
You can use this url to find the more details.
[http://lists.debian.org/debian-gcc/2006/12/msg00244.html](http://lists.debian.org/debian-gcc/2006/12/msg00244.html)

---

