---
title: "Compiling error with missing classmap.h file"
date: 2021-03-28
forum: General Help
---

### Post by tc2020 on 2021-03-28
Hello All,

I compiled a driver source file and got a fatal error saying no such file or directory classmap.h. 

Has anyone experienced this and know how to correct it?. Below shows the steps and error from make command:

```

make -C /lib/modules/5.4.0-1032-raspi/build M= modules
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-1032-raspi'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/confdata.o
  HOSTCC  scripts/kconfig/expr.o
  LEX     scripts/kconfig/lexer.lex.c
  YACC    scripts/kconfig/parser.tab.[ch]
  HOSTCC  scripts/kconfig/lexer.lex.o
  HOSTCC  scripts/kconfig/parser.tab.o
  HOSTCC  scripts/kconfig/preprocess.o
  HOSTCC  scripts/kconfig/symbol.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf  --syncconfig Kconfig
  HOSTCC  scripts/dtc/dtc.o
  HOSTCC  scripts/dtc/flattree.o
  HOSTCC  scripts/dtc/fstree.o
  HOSTCC  scripts/dtc/data.o
  HOSTCC  scripts/dtc/livetree.o
  HOSTCC  scripts/dtc/treesource.o
  HOSTCC  scripts/dtc/srcpos.o
  HOSTCC  scripts/dtc/checks.o
  HOSTCC  scripts/dtc/util.o
  LEX     scripts/dtc/dtc-lexer.lex.c
  YACC    scripts/dtc/dtc-parser.tab.[ch]
  HOSTCC  scripts/dtc/dtc-lexer.lex.o
  HOSTCC  scripts/dtc/dtc-parser.tab.o
  HOSTLD  scripts/dtc/dtc
  HOSTCC  scripts/genksyms/genksyms.o
  YACC    scripts/genksyms/parse.tab.[ch]
  HOSTCC  scripts/genksyms/parse.tab.o
  LEX     scripts/genksyms/lex.lex.c
  HOSTCC  scripts/genksyms/lex.lex.o
  HOSTLD  scripts/genksyms/genksyms
  HOSTCC  scripts/selinux/genheaders/genheaders
scripts/selinux/genheaders/genheaders.c:18:10: fatal error: classmap.h: No such file or directory
   18 | #include "classmap.h"
      |          ^~~~~~~~~~~~
compilation terminated.
make[4]: *** [scripts/Makefile.host:107: scripts/selinux/genheaders/genheaders] Error 1
make[3]: *** [scripts/Makefile.build:518: scripts/selinux/genheaders] Error 2
make[2]: *** [scripts/Makefile.build:518: scripts/selinux] Error 2
make[1]: *** [Makefile:1153: scripts] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-1032-raspi'
make: *** [Makefile:4: all] Error 2

```

I did not get this error previously with earlier version 5.4.0-1029. The current version is:

```

Linux RPi4 5.4.0-1032-raspi #35-Ubuntu SMP PREEMPT Fri Mar 19 20:52:40 UTC 2021 aarch64 aarch64 aarch64 GNU/Linux

```


Any help would be greatly appreciated.  

TC2020

---

### Post by TheFu on 2021-03-30
What library is classmap.h for?  Figure that out, then install the lib{name}-dev package to get the headers.

SELinux isn't really used on Ubuntu/Debian systems. That's a RHEL thing, so in theory, it shouldn't hold up the linking at all.

BTW, the make command appears to have a space in the wrong place. Is that just an artifact of the copy/paste into these forums?

---

### Post by tc2020 on 2021-04-12
TheFu... Sorry for a late reply. I have been away from this topic for the last while, doing something else. I need to get this resolved somehow and will look into your suggestion.  Apparently, others also have this problem, per this link:
[https://bugs.launchpad.net/ubuntu/+source/linux-kernel-headers/+bug/1895470](https://bugs.launchpad.net/ubuntu/+source/linux-kernel-headers/+bug/1895470)

I can avoid compiling this source driver and therefore get around this issue if I can make use of pre-built driver max310x.c. Basically I had to duplicate this driver and renamed it to max310y.c with some minor changes to the source max310x.c. This is where compiling comes in for every kernel update. In this design, I have three uart chips on one spi bus. Two uarts use this max310x.c driver (the third uses prebuilt sc16is752 driver) and I had a hard time getting both to work. By creating max310y.c, it works. Ideally, I 'd like to use max310x.c for both. Any idea?.

---

