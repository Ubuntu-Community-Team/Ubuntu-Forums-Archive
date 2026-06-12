---
title: "problems  to install  Acronis  Echo  Server  for  Linux"
date: 2008-05-06
forum: General Help
---

### Post by balki2005 on 2008-05-06
Hello,

I try to install  Acronis  TrueImageEcho Server  For Linux but  I  have  problems to  compile  the module snapapi26-0.7.29:
when I try  to compile  I recieve  these  error:

```
 dkms build -m snapapi26 -v 0.7.29 -k 2.6.24-17-generic --config /boot/config-2.6.24-17-generic --arch i686 --kernelsourcedir /lib/modules/2.6.24-17-generic/build

Preparing kernel 2.6.24-17-generic for module build:
(This is not compiling a kernel, just preparing kernel symbols)
Storing current .config to be restored when complete
Running Generic preparation routine
make mrproper.....
using /boot/config-2.6.24-17-generic
make oldconfig....(bad exit status: 2)
make prepare....(bad exit status: 2)

Building module:
cleaning build area....
make KERNELRELEASE=2.6.24-17-generic -C /lib/modules/2.6.24-17-generic/build SUBDIRS=/var/lib/dkms/snapapi26/0.7.29/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.24-17-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/snapapi26/0.7.29/build/ for more information.
```



```

 cat  /var/lib/dkms/snapapi26/0.7.29/build/make.log:
DKMS make.log for snapapi26-0.7.29 for kernel 2.6.24-17-generic (i686)
Wed May  7 00:38:37 CEST 2008
make: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


  WARNING: Symbol version dump /usr/src/linux-headers-2.6.24-17-generic/Module.symvers
           is missing; modules will have no dependencies and modversions.

find: /linux: No such file or directory
find: /linux: No such file or directory
scripts/Makefile.build:46: *** CFLAGS was changed in "/var/lib/dkms/snapapi26/0.7.29/build/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make: *** [_module_/var/lib/dkms/snapapi26/0.7.29/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'

```

if  i try what  they  say:

```
jonay@thunderdragon:/usr/src/linux-headers-2.6.24-17-generic$ sudo  make oldconfig && make prepare
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function ‘usage’:
scripts/basic/fixdep.c:131: warning: implicit declaration of function ‘fprintf’
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:131: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function ‘exit’
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘print_cmdline’:
scripts/basic/fixdep.c:140: warning: implicit declaration of function ‘printf’
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: ‘NULL’ undeclared here (not in a function)
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:156: warning: implicit declaration of function ‘realloc’
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function ‘perror’
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:174: warning: implicit declaration of function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:187: warning: implicit declaration of function ‘memcpy’
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:206: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:220: warning: implicit declaration of function ‘tolower’
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:206: warning: unused variable ‘s’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:227: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function ‘ntohl’
scripts/basic/fixdep.c:244: warning: implicit declaration of function ‘isalnum’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:261: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:272: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:276: warning: implicit declaration of function ‘open’
scripts/basic/fixdep.c:276: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:278: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:282: warning: implicit declaration of function ‘fstat’
scripts/basic/fixdep.c:284: warning: implicit declaration of function ‘close’
scripts/basic/fixdep.c:287: warning: implicit declaration of function ‘mmap’
scripts/basic/fixdep.c:287: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:296: warning: implicit declaration of function ‘munmap’
scripts/basic/fixdep.c:272: warning: unused variable ‘st’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:304: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function ‘strchr’
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function ‘strchr’
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:310: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:306: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:343: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:347: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:349: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:359: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:343: warning: unused variable ‘st’
scripts/basic/fixdep.c: In function ‘traps’:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:378: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
jonay@thunderdragon:/usr/src/linux-headers-2.6.24-17-generic$
```

who  can  help  me ?

thanks in advance,

Jonay

---

