---
title: "Compile error"
date: 2007-03-02
forum: General Help
---

### Post by Currahee on 2007-03-02
I'm trying to compile from source netsukuku-0.0.9b but I'm getting this when try to:

```
xxx@Linux:~/Softwares/Tbz2/netsukuku-0.0.9b$ make
Making all in src
make[1]: Entering directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src'
make  all-recursive
make[2]: Entering directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src'
Making all in man
make[3]: Entering directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src/man'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src/man'
Making all in scripts
make[3]: Entering directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src/scripts'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src/scripts'
Making all in conf
make[3]: Entering directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src/conf'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src/conf'
make[3]: Entering directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -I.  -I -g -O2 -MT accept.o -MD -MP -MF ".deps/accept.Tpo" -c -o accept.o accept.c; \
        then mv -f ".deps/accept.Tpo" ".deps/accept.Po"; else rm -f ".deps/accept.Tpo"; exit 1; fi
In file included from accept.c:29:
includes.h:31:24: error: asm/bitops.h: Nessun file o directory
make[3]: *** [accept.o] Error 1
make[3]: Leaving directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/xxx/Softwares/Tbz2/netsukuku-0.0.9b/src'
make: *** [all-recursive] Error 1

```
Please help...

---

### Post by eeried on 2007-06-11
> But SCons is cooler:
[http://www.scons.org/](http://www.scons.org/)
(You should have installed at least the 2.4 version of Python in order to
avoid dirty bugs in scons)

This is what I read on the Netsukuku web site.

I'm sorry I can't help you but I'd like to to point out this topic. Netsukuku looks very interesting!

---

### Post by 444 on 2007-06-11
linux-headers package.

---

