---
title: "can't compile kernel"
date: 2007-02-01
forum: General Help
---

### Post by GNUtoo on 2007-02-01
i have ubuntu 6.10
# uname -a
Linux port3 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

# apt-get install linux-headers-2.6.17-10-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-headers-2.6.17-10-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/909kB of archives.
After unpacking 24.7MB of additional disk space will be used.
Selecting previously deselected package linux-headers-2.6.17-10-generic.
(Reading database ... 82862 files and directories currently installed.)
Unpacking linux-headers-2.6.17-10-generic (from .../linux-headers-2.6.17-10-generic_2.6.17.1-10.34_i386.deb) ...
Setting up linux-headers-2.6.17-10-generic (2.6.17.1-10.34) ...

root@port3:/usr/src/linux-headers-2.6.17-10-generic# make
  CHK     include/linux/version.h
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function ‘usage’:
scripts/basic/fixdep.c:129: warning: implicit declaration of function ‘fprintf’
scripts/basic/fixdep.c:129: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:129: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function ‘exit’
scripts/basic/fixdep.c:130: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘print_cmdline’:
scripts/basic/fixdep.c:138: warning: implicit declaration of function ‘printf’
scripts/basic/fixdep.c:138: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:141: error: ‘NULL’ undeclared here (not in a function)
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:154: warning: implicit declaration of function ‘realloc’
scripts/basic/fixdep.c:154: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:156: warning: implicit declaration of function ‘perror’
scripts/basic/fixdep.c:156: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:172: warning: implicit declaration of function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:185: warning: implicit declaration of function ‘memcpy’
scripts/basic/fixdep.c:185: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:204: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:212: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:218: warning: implicit declaration of function ‘tolower’
scripts/basic/fixdep.c:220: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:204: warning: unused variable ‘s’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:223: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:225: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:231: warning: implicit declaration of function ‘ntohl’
scripts/basic/fixdep.c:242: warning: implicit declaration of function ‘isalnum’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:255: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:255: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:266: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:270: warning: implicit declaration of function ‘open’
scripts/basic/fixdep.c:270: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:272: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:272: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:274: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:276: warning: implicit declaration of function ‘fstat’
scripts/basic/fixdep.c:278: warning: implicit declaration of function ‘close’
scripts/basic/fixdep.c:281: warning: implicit declaration of function ‘mmap’
scripts/basic/fixdep.c:281: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:288: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:290: warning: implicit declaration of function ‘munmap’
scripts/basic/fixdep.c:266: warning: unused variable ‘st’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:295: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:298: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:300: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:302: warning: implicit declaration of function ‘strchr’
scripts/basic/fixdep.c:302: warning: incompatible implicit declaration of built-in function ‘strchr’
scripts/basic/fixdep.c:304: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:304: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:305: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:307: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:300: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:337: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:341: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:343: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:343: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:345: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:353: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:360: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:337: warning: unused variable ‘st’
scripts/basic/fixdep.c: In function ‘traps’:
scripts/basic/fixdep.c:372: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:372: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:374: warning: incompatible implicit declaration of built-in function ‘exit’
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make: *** [include/linux/autoconf.h] Error 2

make xconfig,make menuconfig make config and make oldconfig doesn't work

i need to be able to recompile the kernel in order to install the madwifi+openhal module

---

### Post by lloyd_b on 2007-02-01
It looks like you're missing the "libc6-dev" package, which contains all of those ".h" files that it's complaining about.
 
Which makes me wonder if the build system on your machine is entirely sane.  I would suggest "sudo apt-get install build-essential", which should install the libc6-dev package, as well as anything else that's missing.

Lloyd B.

---

