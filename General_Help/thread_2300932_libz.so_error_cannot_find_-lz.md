---
title: "libz.so error cannot find -lz"
date: 2015-10-29
forum: General Help
---

### Post by waza123 on 2015-10-29
I installed all possible libz librarys and still can't compile. Please help, what to install to fix the problem !?


Ubuntu 13.10

> /usr/bin/ld: skipping incompatible /usr/local/lib/libz.so when searching for -lz
/usr/bin/ld: skipping incompatible /usr/local/lib/libz.a when searching for -lz
/usr/bin/ld: cannot find -lz
collect2: error: ld returned 1 exit status
Build failed.


> $ locate libz.so
/usr/lib/libz.so.1
/usr/lib/x86_64-linux-gnu/libz.so
/usr/local/lib/libz.so
/usr/local/lib/libz.so.1
/usr/local/lib/libz.so.1.2.8

> apt-get install zlib1g
apt-get install lib32z1

---

### Post by Toz on 2015-10-29
If you're compiling, you need to install the "-dev" versions of the packages. Either "lib64z1-dev" or "zlib1g-dev".

You should also probably do something about the incompatible ligz.so install you have in /usr/local/lib so it doesn't interfere.

---

### Post by sandyd on 2015-10-29
Side Note: Ubuntu 13.10 is no longer supported and is no longer updated or available in the standard repositories since July 17, 2014

---

### Post by waza123 on 2015-10-29
problem solved. by reinstalling (removed before) gcc g++ 4.7 completely

apt-get install gcc-4.7-multilib
apt-get install g++-4.7-multilib

topic closed.

---

### Post by oldos2er on 2015-10-29
Please upgrade to a supported version of Ubuntu.

Closed.

---

