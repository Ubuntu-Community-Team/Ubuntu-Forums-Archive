---
title: "Ubuntu GCC 4.0.1 kernel compile problems"
date: 2005-06-10
forum: General Help
---

### Post by Vertical on 2005-06-10
Hello

When I want to compile any kernel in my Ubuntu 5.10 (gcc 4.0.1), typing 'make xconfig' (or make menuconfig), I get:

```
root@fujitsu-m:/usr/src/linux-2.6.11.11 # make xconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux/4.0.1/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux/4.0.1/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux/4.0.1/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function 'usage':
scripts/basic/fixdep.c:129: warning: implicit declaration of function 'fprintf'
scripts/basic/fixdep.c:129: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:129: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function 'exit'
scripts/basic/fixdep.c:130: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c: In function 'print_cmdline':
scripts/basic/fixdep.c:135: warning: implicit declaration of function 'printf'
scripts/basic/fixdep.c:135: warning: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:138: error: 'NULL' undeclared here (not in a function)
scripts/basic/fixdep.c: In function 'grow_config':
scripts/basic/fixdep.c:151: warning: implicit declaration of function 'realloc'
scripts/basic/fixdep.c:151: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:153: warning: implicit declaration of function 'perror'
scripts/basic/fixdep.c:153: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c: In function 'is_defined_config':
scripts/basic/fixdep.c:169: warning: implicit declaration of function 'memcmp'
scripts/basic/fixdep.c: In function 'define_config':
scripts/basic/fixdep.c:182: warning: implicit declaration of function 'memcpy'
scripts/basic/fixdep.c:182: warning: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c: In function 'use_config':
scripts/basic/fixdep.c:201: error: 'PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:209: warning: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c:215: warning: implicit declaration of function 'tolower'
scripts/basic/fixdep.c:217: warning: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c:201: warning: unused variable 's'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:220: error: parse error before 'size_t'
scripts/basic/fixdep.c:221: warning: function declaration isn't a prototype
scripts/basic/fixdep.c: In function 'parse_config_file':
scripts/basic/fixdep.c:222: error: 'map' undeclared (first use in this function)scripts/basic/fixdep.c:222: error: 'len' undeclared (first use in this function)scripts/basic/fixdep.c:228: warning: implicit declaration of function 'ntohl'
scripts/basic/fixdep.c:239: warning: implicit declaration of function 'isalnum'
scripts/basic/fixdep.c:245: warning: pointer targets in passing argument 1 of 'use_config' differ in signedness
scripts/basic/fixdep.c: In function 'strrcmp':
scripts/basic/fixdep.c:252: warning: implicit declaration of function 'strlen'
scripts/basic/fixdep.c:252: warning: incompatible implicit declaration of built-in function 'strlen'
scripts/basic/fixdep.c: In function 'do_config_file':
scripts/basic/fixdep.c:263: error: storage size of 'st' isn't known
scripts/basic/fixdep.c:267: warning: implicit declaration of function 'open'
scripts/basic/fixdep.c:267: error: 'O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:269: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:269: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:271: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:273: warning: implicit declaration of function 'fstat'
scripts/basic/fixdep.c:275: warning: implicit declaration of function 'close'
scripts/basic/fixdep.c:278: warning: implicit declaration of function 'mmap'
scripts/basic/fixdep.c:278: error: 'PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:278: error: 'MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:287: warning: implicit declaration of function 'munmap'
scripts/basic/fixdep.c:263: warning: unused variable 'st'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:292: error: parse error before 'size_t'
scripts/basic/fixdep.c:293: warning: function declaration isn't a prototype
scripts/basic/fixdep.c: In function 'parse_dep_file':
scripts/basic/fixdep.c:294: error: 'map' undeclared (first use in this function)scripts/basic/fixdep.c:295: error: 'len' undeclared (first use in this function)scripts/basic/fixdep.c:297: error: 'PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:299: warning: implicit declaration of function 'strchr'
scripts/basic/fixdep.c:299: warning: incompatible implicit declaration of built-in function 'strchr'
scripts/basic/fixdep.c:299: warning: pointer targets in passing argument 1 of 'strchr' differ in signedness
scripts/basic/fixdep.c:299: warning: pointer targets in assignment differ in signedness
scripts/basic/fixdep.c:301: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:301: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:302: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:304: warning: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c:305: warning: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c:297: warning: unused variable 's'
scripts/basic/fixdep.c: In function 'print_deps':
scripts/basic/fixdep.c:334: error: storage size of 'st' isn't known
scripts/basic/fixdep.c:338: error: 'O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:340: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:340: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:342: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:346: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:350: error: 'PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:350: error: 'MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:350: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:334: warning: unused variable 'st'
scripts/basic/fixdep.c: In function 'traps':
scripts/basic/fixdep.c:369: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:369: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:371: warning: incompatible implicit declaration of built-in function 'exit'
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

```

Also, I can't change to GCC 3.xx, cause of dependencies.
How to fix GCC?

---

### Post by minio on 2005-06-10
It looks like you are missing some header files. libc6-dev package maybe?

---

### Post by Vertical on 2005-06-11
[http://ubuntuforums.org/showthread.php?p=208771#post208771](http://ubuntuforums.org/showthread.php?p=208771#post208771)

Sorry for posting to wrong thread

---

