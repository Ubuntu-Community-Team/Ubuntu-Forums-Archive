---
title: "Failed to build ctags-5.8 ."
date: 2023-11-21
forum: General Help
---

### Post by jiapei100 on 2023-11-21
Can anybody help to take a look? Thank you ...
I'm using **Ubuntu 22.04.3** with **gcc 11.4.0** from default repo.

```

&#10140;  ctags-5.8 make -j12
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c args.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c ant.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c asm.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c asp.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c awk.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c basic.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c beta.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c c.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c cobol.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c dosbatch.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c eiffel.c
gcc -I. -I. -DHAVE_CONFIG_H -g -O2 -c entry.c
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from ant.c:17:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from asm.c:18:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/stdio.h:27,
                 from args.c:17:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from asp.c:18:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from awk.c:17:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from beta.c:20:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from basic.c:20:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/stdlib.h:26,
                 from vstring.h:20,
                 from strlist.h:19,
                 from parse.h:19,
                 from cobol.c:17:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from dosbatch.c:17:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from eiffel.c:21:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from entry.c:17:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
In file included from /usr/include/features.h:486,
                 from /usr/include/x86_64-linux-gnu/bits/libc-header-start.h:33,
                 from /usr/include/string.h:26,
                 from c.c:18:
/usr/include/x86_64-linux-gnu/sys/cdefs.h:320:61: error: missing ')' after "__has_attribute"
  320 | #if __GNUC_PREREQ (2,7) || __glibc_has_attribute (__unused__)
      |                                                             ^
general.h:60:36: error: missing binary operator before token "("
   60 | # define __unused__  __attribute__((unused))
      |                                    ^
make: *** [Makefile:220: ant.o] Error 1
make: *** Waiting for unfinished jobs....
make: *** [Makefile:220: cobol.o] Error 1
make: *** [Makefile:220: dosbatch.o] Error 1
make: *** [Makefile:220: awk.o] Error 1
make: *** [Makefile:220: eiffel.o] Error 1
make: *** [Makefile:220: asm.o] Error 1
make: *** [Makefile:220: beta.o] Error 1
make: *** [Makefile:220: args.o] Error 1
make: *** [Makefile:220: asp.o] Error 1
make: *** [Makefile:220: basic.o] Error 1
make: *** [Makefile:220: entry.o] Error 1
make: *** [Makefile:220: c.o] Error 1
&#10140;  ctags-5.8 gcc --version
gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
Copyright (C) 2021 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

&#10140;  ctags-5.8 g++ --version
g++ (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
Copyright (C) 2021 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

&#10140;  ctags-5.8 


```

---

### Post by norobro on 2023-11-22
Is there a reason you're not using the version in the repo? [https://packages.ubuntu.com/jammy/exuberant-ctags](https://packages.ubuntu.com/jammy/exuberant-ctags)


Browsing the changelog there is this:> * d/p/use-conventional-unused-marker.patch: Fix FTBFS against glibc 2.34FTBFS is Failure To Build From Source.


Then at the top of the patch file use-conventional-unused-marker.patch:> The `__unused` macro has been used on Linux systems for this exact
purpose for ages. On the other hand, using the non-standard __unused__
breaks the build when compiling against glibc 2.34, as they use this
identifier internally.



So if you need to build exuberant-ctags it seems you will need to patch or modify the source.

---

