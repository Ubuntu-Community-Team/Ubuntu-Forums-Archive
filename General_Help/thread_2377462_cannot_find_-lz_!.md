---
title: "cannot find -lz ?!"
date: 2017-11-13
forum: General Help
---

### Post by fairbird on 2017-11-13
I move to Ubuntu 16.04 and I have tried ti build amd install some package 
([COLOR=#282828][FONT=helvetica]Makefile.am) include
[/FONT][/COLOR]```
[COLOR=#000000]blackholesocker_LDADD [/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000] $[/COLOR][COLOR=#666600]([/COLOR][COLOR=#000000]OPENMP_CFLAGS[/COLOR][COLOR=#666600])[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]lz[/COLOR]
```

But I got this error
```
 DEBUG: SITE files ['endian-little', 'bit-32', 'mips-common', 'common-linux', 'common-glibc', 'mipsel-linux', 'common']| DEBUG: Executing shell function do_compile
| NOTE: make -j 4
| mipsel-oe-linux-gcc  -mel -mabi=32 -msoft-float -march=mips32 --sysroot=/home/rr/pli-oe-core/build_dm800/tmp/work/dm800-oe-linux/blackholesocker/0.1-r1/recipe-sysroot -fopenmp -Os -pipe -g -feliminate-unused-debug-types -fdebug-prefix-map=/home/rr/pli-oe-core/build_dm800/tmp/work/dm800-oe-linux/blackholesocker/0.1-r1=/usr/src/debug/blackholesocker/0.1-r1 -fdebug-prefix-map=/home/rr/pli-oe-core/build_dm800/tmp/work/dm800-oe-linux/blackholesocker/0.1-r1/recipe-sysroot-native= -fdebug-prefix-map=/home/rr/pli-oe-core/build_dm800/tmp/work/dm800-oe-linux/blackholesocker/0.1-r1/recipe-sysroot=   -Wl,-O1  -Wl,--as-needed -o blackholesocker blackholesocker-main.o -fopenmp -lz
| /home/rr/pli-oe-core/build_dm800/tmp/work/dm800-oe-linux/blackholesocker/0.1-r1/recipe-sysroot-native/usr/bin/mipsel-oe-linux/../../libexec/mipsel-oe-linux/gcc/mipsel-oe-linux/7.2.0/ld: cannot find -lz
| collect2: error: ld returned 1 exit status
| Makefile:358: recipe for target 'blackholesocker' failed 
| make: *** [blackholesocker] Error 1
```

How to  fix it ?!
Thank you

---

### Post by fairbird on 2017-11-14
Solved ..
By adding 
```
DEPENDS = "zlib"
```

---

