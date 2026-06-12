---
title: "no gcc binary"
date: 2006-10-11
forum: General Help
---

### Post by hiCountryCowboy on 2006-10-11
1. A fresh install of Dapper
2. apt-get of build-essentials,
3. lrwxrwxrwx 1 root root 7 2006-10-11 11:14 /usr/bin/gcc -> gcc-4.0
4. NO gcc-4.0 to be found!!!

ergo: no compiler!!!

---

### Post by meng on 2006-10-11
Just checking, you did
apt-get install build-essential
correct? It's not essential_s_

---

### Post by hiCountryCowboy on 2006-10-11
YUP, but I have been banging the devil out this box as I have a bunch of developing to do!

So...

1. apt-get remove build-essential
2. apt-get install gcc-4.0.-base
3. apt-get install gcc-4.0
4. apt-get install build-essential

Order seems to be the issue.  One has to load the 'base' portion of the compiler first, but that doesn't actually install the compiler.  Then install  the compiler, and finally the build-essential.  I may have missed something along the way, but at least with this method, I'm up and compiling!!!

---

