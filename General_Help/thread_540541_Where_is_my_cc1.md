---
title: "Where is my cc1 ?"
date: 2007-09-01
forum: General Help
---

### Post by Martin12 on 2007-09-01
I'm using a 7.04 system,with gcc and cpp installed but I'm unable to compile a simple C-programm:

m12@ubuntu:~$ gcc -v test.c
Es werden eingebaute Spezifikationen verwendet.
Ziel: i486-linux-gnu
Konfiguriert mit: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread-Modell: posix
gcc-Version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
cc1 -quiet -v test.c -quiet -dumpbase test.c -mtune=generic -auxbase test -version -fstack-protector -fstack-protector -o /tmp/ccZvzQL3.s
gcc: error trying to exec 'cc1': execvp: No such file or directory

That is  true: I do not have "cc1" on my system and it is not part of the
cpp package:

$dpkg -L cpp-4.1
/.
/usr
/usr/share
/usr/share/doc
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/cpp-4.1.1.gz
/usr/bin
/usr/bin/cpp-4.1
/usr/lib
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu
/usr/lib/gcc/i486-linux-gnu/4.1.2
/usr/share/doc/cpp-4.1
/usr/share/man/man1/i486-linux-gnu-cpp-4.1.1.gz
/usr/bin/i486-linux-gnu-cpp-4.1


The corresponding debian-package (cpp-4.1 from stable), however,  comprises the file
/usr/lib/gcc/i486-linux-gnu/4.1.2/cc1


Does anyone have the "cc1" on ubuntu 7.04? If so, where did you get if from ?

Here is my configuration:

ii cpp 4.1.2-1ubuntu1
ii cpp-4.1 4.1.2-0ubuntu4
ii gcc 4.1.2-1ubuntu1
ii gcc-4.1 4.1.2-0ubuntu4
ii gcc-4.1-base 4.1.2-0ubuntu4


-Martin

---

### Post by taurus on 2007-09-01
Did you install gcc by itself or did you install the build-essential package?

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by Martin12 on 2007-09-02
> **taurus said:**
> Did you install gcc by itself or did you install the build-essential package?

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

That does not matter. ```
build-essential
``` does not contain any package that provides cc1.

---

### Post by Martin12 on 2007-09-07
solved by re-installing cpp

---

