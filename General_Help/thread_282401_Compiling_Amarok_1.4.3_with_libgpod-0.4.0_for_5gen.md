---
title: "Compiling Amarok 1.4.3 with libgpod-0.4.0 for 5gen iPod"
date: 2006-10-22
forum: General Help
---

### Post by nick.seifert on 2006-10-22
Since my 5Gen iPod doesn't seem to show album art i've been trying to compile Amarok 1.4.3 from source and include libgpod-0.4.0. I guess i have several questions.  First, is there a KDE distribution of libgpod-0.4.0 out there?

I haven't found one, so i'm trying to compile it.  I'm able to ./configure it, but then when i make, i get errors.

root@nick-desktop:~/libgpod/libgpod-0.4.0# make
make  all-recursive
make[1]: Entering directory `/home/nick/libgpod/libgpod-0.4.0'
Making all in src
make[2]: Entering directory `/home/nick/libgpod/libgpod-0.4.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/nick/libgpod/libgpod-0.4.0/src'
Making all in bindings
make[2]: Entering directory `/home/nick/libgpod/libgpod-0.4.0/bindings'
Making all in python
make[3]: Entering directory `/home/nick/libgpod/libgpod-0.4.0/bindings/python'
Making all in examples
make[4]: Entering directory `/home/nick/libgpod/libgpod-0.4.0/bindings/python/examples'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/nick/libgpod/libgpod-0.4.0/bindings/python/examples'
make[4]: Entering directory `/home/nick/libgpod/libgpod-0.4.0/bindings/python'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/nick/libgpod/libgpod-0.4.0/bindings/python'
make[3]: Leaving directory `/home/nick/libgpod/libgpod-0.4.0/bindings/python'
make[3]: Entering directory `/home/nick/libgpod/libgpod-0.4.0/bindings'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/nick/libgpod/libgpod-0.4.0/bindings'
make[2]: Leaving directory `/home/nick/libgpod/libgpod-0.4.0/bindings'
Making all in tests
make[2]: Entering directory `/home/nick/libgpod/libgpod-0.4.0/tests'
/bin/sh ../libtool --mode=link gcc  -g -O2   -o test-init-ipod    -lgobject-2.0 -lglib-2.0    ../src/libgpod.la
gcc -g -O2 -o .libs/test-init-ipod  /usr/lib/libgobject-2.0.so /usr/lib/libglib-2.0.so ../src/.libs/libgpod.so -Wl,--rpath -Wl,/usr/local/lib
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
make[2]: *** [test-init-ipod] Error 1
make[2]: Leaving directory `/home/nick/libgpod/libgpod-0.4.0/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nick/libgpod/libgpod-0.4.0'
make: *** [all] Error 2


A similar error appears if i try to make install.
When i ./configure Amarok it doesn't show that it will include iPod support, therefor i'm assuming that the above error is the cause.

I'm pretty inexperienced with Kubuntu but really want to learn, so please help!

---

### Post by nick.seifert on 2006-10-22
The fix seemed to be to download support for Fortran 77 compiling.  I used synaptic to do so.  Ran ./configure again and the errors went away.

---

