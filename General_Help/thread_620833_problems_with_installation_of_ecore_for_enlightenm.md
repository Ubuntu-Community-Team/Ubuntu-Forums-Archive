---
title: "problems with installation of ecore for enlightenment"
date: 2007-11-23
forum: General Help
---

### Post by yotama9 on 2007-11-23
Hi

I've just installed enlightenment and as I'm trying to install entropy file browser I'm installing the efl's.

Installation of ecore gave me some trubles tho:

```
yotam@yotam-laptop:~/e17_cvs/e17/libs/ecore$ sudo make install
Making install in src
make[1]: Entering directory `/home/yotam/e17_cvs/e17/libs/ecore/src'
Making install in lib
make[2]: Entering directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib'
Making install in ecore
make[3]: Entering directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib/ecore'
make[4]: Entering directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib/ecore'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libecore.la' '/usr/local/lib/libecore.la'
/usr/bin/install -c .libs/libecore.so.0.9.9 /usr/local/lib/libecore.so.0.9.9
(cd /usr/local/lib && { ln -s -f libecore.so.0.9.9 libecore.so.0 || { rm -f libecore.so.0 && ln -s libecore.so.0.9.9 libecore.so.0; }; })
(cd /usr/local/lib && { ln -s -f libecore.so.0.9.9 libecore.so || { rm -f libecore.so && ln -s libecore.so.0.9.9 libecore.so; }; })
/usr/bin/install -c .libs/libecore.lai /usr/local/lib/libecore.la
/usr/bin/install -c .libs/libecore.a /usr/local/lib/libecore.a
chmod 644 /usr/local/lib/libecore.a
ranlib /usr/local/lib/libecore.a
libtool: install: warning: remember to run `libtool --finish /opt/e17/lib'
test -z "/usr/local/include" || mkdir -p -- "/usr/local/include"
 /usr/bin/install -c -m 644 'Ecore.h' '/usr/local/include/Ecore.h'
 /usr/bin/install -c -m 644 'Ecore_Data.h' '/usr/local/include/Ecore_Data.h'
 /usr/bin/install -c -m 644 'Ecore_Str.h' '/usr/local/include/Ecore_Str.h'
make[4]: Leaving directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib/ecore'
make[3]: Leaving directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib/ecore'
Making install in ecore_job
make[3]: Entering directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib/ecore_job'
make[4]: Entering directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib/ecore_job'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'libecore_job.la' '/usr/local/lib/libecore_job.la'
libtool: install: error: cannot install `libecore_job.la' to a directory not ending in /opt/e17/lib
make[4]: *** [install-libLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib/ecore_job'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib/ecore_job'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/yotam/e17_cvs/e17/libs/ecore/src/lib'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/yotam/e17_cvs/e17/libs/ecore/src'
make: *** [install-recursive] Error 1
yotam@yotam-laptop:~/e17_cvs/e17/libs/ecore$ 
```

I've noticed this line:
```
libtool: install: warning: remember to run `libtool --finish /opt/e17/lib'
```

but I don't konw what to do with it. (I tried simply running the line but it didn't help)

any Idea?

thanks.

---

