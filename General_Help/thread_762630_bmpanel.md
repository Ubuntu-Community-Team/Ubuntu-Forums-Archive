---
title: "bmpanel"
date: 2008-04-22
forum: General Help
---

### Post by mossgarden on 2008-04-22
I've been trying to install bmpanel for Pekwm and after few difficulties I got this far:

```
scons: Reading SConscript files ...
Checking for C header file stdio.h... yes
Checking for C header file stdarg.h... yes
Checking for C header file stdlib.h... yes
Checking for C header file string.h... yes
Checking for C header file signal.h... yes
Checking for C header file sys/time.h... yes
Checking for C header file sys/types.h... yes
Checking for C header file unistd.h... yes
Checking for C header file dirent.h... yes
Checking for C header file time.h... yes
Checking for C library ev... yes
Checking for pkg-config >= 0.20... yes
Checking for imlib2... yes
scons: done reading SConscript files.
scons: Building targets ...
Compiler Flags: -std=c99 -Wall -DPREFIX=\"/usr\" -O2 -march=native
Libs: ev, Imlib2
  C: src/common.c
[b]src/common.c:1: error: bad value (native) for -march= switch
src/common.c:1: error: bad value (native) for -mtune= switch
scons: *** [build/src/common.o] Error 1
scons: building terminated because of errors.[/b]
```

My question would be what's wrong, because I don't understand (of course it might be that I'm total noob but anyway...)? (I have Ubuntu 7.10)

---

