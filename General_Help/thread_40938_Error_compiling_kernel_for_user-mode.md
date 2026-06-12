---
title: "Error compiling kernel for user-mode"
date: 2005-06-11
forum: General Help
---

### Post by shmk on 2005-06-11
I'm trying to compile kernel for install user-mode-linux

I have kernel 2.6.10-5-386 so I downloaded linux-source-2.6.10 from synaptec

After I copied linux-source-2.6.10.tar.bz2 on /usr/src/uml and extracted it.
Then I entered on the directory with the source and typed:

"make xconfig ARCH=um"

And the make fails returning these lines of error:
```
 HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: stdio.h: No such file or directory
In file included from /usr/lib/gcc-lib/i486-linux/3.3.5/include/syslimits.h:7,
                 from /usr/lib/gcc-lib/i486-linux/3.3.5/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc-lib/i486-linux/3.3.5/include/limits.h:122:75: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function `usage':
scripts/basic/fixdep.c:129: warning: implicit declaration of function `fprintf'
scripts/basic/fixdep.c:129: error: `stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function `exit'
scripts/basic/fixdep.c: In function `print_cmdline':
scripts/basic/fixdep.c:135: warning: implicit declaration of function `printf'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:138: error: `NULL' undeclared here (not in a function)
scripts/basic/fixdep.c: In function `grow_config':
scripts/basic/fixdep.c:151: warning: implicit declaration of function `realloc'
scripts/basic/fixdep.c:151: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:152: error: `NULL' undeclared (first use in this function)
scripts/basic/fixdep.c:153: warning: implicit declaration of function `perror'
scripts/basic/fixdep.c: In function `is_defined_config':
scripts/basic/fixdep.c:169: warning: implicit declaration of function `memcmp'
scripts/basic/fixdep.c: In function `define_config':
scripts/basic/fixdep.c:182: warning: implicit declaration of function `memcpy'
scripts/basic/fixdep.c: In function `use_config':
scripts/basic/fixdep.c:201: error: `PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:215: warning: implicit declaration of function `tolower'
scripts/basic/fixdep.c:201: warning: unused variable `s'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:220: error: syntax error before "size_t"
scripts/basic/fixdep.c:221: warning: function declaration isn't a prototype
scripts/basic/fixdep.c: In function `parse_config_file':
scripts/basic/fixdep.c:222: error: `map' undeclared (first use in this function)
scripts/basic/fixdep.c:222: error: `len' undeclared (first use in this function)
scripts/basic/fixdep.c:228: warning: implicit declaration of function `ntohl'
scripts/basic/fixdep.c:239: warning: implicit declaration of function `isalnum'
scripts/basic/fixdep.c: In function `strrcmp':
scripts/basic/fixdep.c:252: warning: implicit declaration of function `strlen'
scripts/basic/fixdep.c: In function `do_config_file':
scripts/basic/fixdep.c:263: error: storage size of `st' isn't known
scripts/basic/fixdep.c:267: warning: implicit declaration of function `open'
scripts/basic/fixdep.c:267: error: `O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:269: error: `stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:273: warning: implicit declaration of function `fstat'
scripts/basic/fixdep.c:275: warning: implicit declaration of function `close'
scripts/basic/fixdep.c:278: warning: implicit declaration of function `mmap'
scripts/basic/fixdep.c:278: error: `NULL' undeclared (first use in this function)
scripts/basic/fixdep.c:278: error: `PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:278: error: `MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:287: warning: implicit declaration of function `munmap'
scripts/basic/fixdep.c:263: warning: unused variable `st'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:292: error: syntax error before "size_t"
scripts/basic/fixdep.c:293: warning: function declaration isn't a prototype
scripts/basic/fixdep.c: In function `parse_dep_file':
scripts/basic/fixdep.c:294: error: `map' undeclared (first use in this function)
scripts/basic/fixdep.c:295: error: `len' undeclared (first use in this function)
scripts/basic/fixdep.c:297: error: `PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:299: warning: implicit declaration of function `strchr'
scripts/basic/fixdep.c:301: error: `stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:297: warning: unused variable `s'
scripts/basic/fixdep.c: In function `print_deps':
scripts/basic/fixdep.c:334: error: storage size of `st' isn't known
scripts/basic/fixdep.c:338: error: `O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:340: error: `stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:350: error: `NULL' undeclared (first use in this function)
scripts/basic/fixdep.c:350: error: `PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:350: error: `MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:350: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:334: warning: unused variable `st'
scripts/basic/fixdep.c: In function `traps':
scripts/basic/fixdep.c:369: error: `stderr' undeclared (first use in this function)
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
```

Someone can give me an hand ?  :???:

---

