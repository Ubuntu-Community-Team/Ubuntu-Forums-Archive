---
title: "gcc-3.4 issues on Dapper"
date: 2006-10-09
forum: General Help
---

### Post by serendipitousus on 2006-10-09
Hello all,

I am on an almost fresh installation of Dapper Drake. I have apt-gotten the compiler gcc-3.4, which is needed for a certain piece of software that I am installing. The actual version I have is Ubuntu 3.4.6-1ubuntu2. 

When I create a simple file 
int main (){return 0;}
and try to compile, I get the error message

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

I have tried removing and reinstalling gcc-3.4.

Does anyone have thoughts as to why I do not have this file, where it comes from, or how I can get it?

---

### Post by lamego on 2006-10-09
You need to install:
libc6-dev

Anyway you should install: build-essential

---

### Post by serendipitousus on 2006-10-09
Wow. You guys are amazingly quick. Thanks so much for the save.

---

