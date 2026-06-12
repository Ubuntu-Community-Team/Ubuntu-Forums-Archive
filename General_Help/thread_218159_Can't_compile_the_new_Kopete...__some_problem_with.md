---
title: "Can't compile the new Kopete...  some problem with gcc"
date: 2006-07-18
forum: General Help
---

### Post by Starlight on 2006-07-18
Hi! I can't compile the new Kopete. :( I get a weird error when I run sudo ./configure. 

It's some weird error with gcc... here's a fragment of the config.log file with the error:

```

configure:3209: checking for gcc
configure:3225: found /usr/bin/gcc
configure:3236: result: gcc
configure:3474: checking for C compiler version
configure:3481: gcc --version >&5
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3484: $? = 0
configure:3491: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
configure:3494: $? = 0
configure:3501: gcc -V >&5
gcc: '-V' option must have argument
configure:3504: $? = 1
configure:3527: checking for C compiler default output file name
configure:3554: gcc     conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:3557: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "kopete-0.12.1"
| #define VERSION "3.5.3"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3596: error: C compiler cannot create executables
See `config.log' for more details.

```

---

### Post by Sef on 2006-07-18
Have you installed build-essential? 

If not, then follow these directions:

Ubuntu: sudo apt-get update
        sudo aptitude install build-essential

Kubuntu: kdesu apt-get update
         kdesu aptitude install build-essential

---

### Post by Starlight on 2006-07-18
Thanks! I don't have it installed, but I'm downloading it now. I hope it will work then! :)

---

