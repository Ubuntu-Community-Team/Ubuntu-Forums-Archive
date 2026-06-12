---
title: "copyfs and LZOlayer_fs compile problem"
date: 2007-03-29
forum: General Help
---

### Post by bugmenot_user on 2007-03-29
I can't compile [CopyFs]("http://n0x.org/copyfs/") and [LZOlayer_fs]("http://north.one.pl/~kazik/pub/LZOlayer/") on dapper. 
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
copyfs gives these output
```
$ ./configure
creating cache ./config.cache
checking for gcc... gcc
checking whether the C compiler (gcc ) works... yes
checking whether the C compiler (gcc ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for fuse_main in -lfuse... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for fcntl.h... yes
checking for strings.h... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for attr/xattr.h... no
checking for working const... yes
checking for uid_t in sys/types.h... yes
checking for mode_t... yes
checking for off_t... yes
checking for size_t... yes
checking whether utime accepts a null argument... yes
checking for mkdir... yes
checking for strdup... yes
checking for lsetxattr... yes
checking for lgetxattr... yes
checking for llistxattr... yes
updating cache ./config.cache
creating ./config.status
creating Makefile

$ make
gcc -Wall -ansi -W -std=c99 -g -ggdb -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -c -o ea.o ea.c
ea.c:11:24: error: attr/xattr.h: No such file or directory
ea.c:15:18: error: fuse.h: No such file or directory
ea.c: In function 'callback_setxattr':
ea.c:46: error: 'ENOENT' undeclared (first use in this function)
ea.c:46: error: (Each undeclared identifier is reported only once
ea.c:46: error: for each function it appears in.)
ea.c:65: error: 'EINVAL' undeclared (first use in this function)
ea.c:89: warning: implicit declaration of function 'fuse_get_context'
ea.c:89: warning: assignment makes pointer from integer without a cast
ea.c:90: error: dereferencing pointer to incomplete type
ea.c:90: error: dereferencing pointer to incomplete type
ea.c:91: error: 'EACCES' undeclared (first use in this function)
ea.c:98: error: 'errno' undeclared (first use in this function)
ea.c:111: error: 'EPERM' undeclared (first use in this function)
ea.c:121: warning: implicit declaration of function 'lsetxattr'
ea.c:126: warning: control reaches end of non-void function
ea.c: In function 'callback_getxattr':
ea.c:139: error: 'ENOENT' undeclared (first use in this function)
ea.c:164: error: 'ERANGE' undeclared (first use in this function)
ea.c:213: error: 'ENOMEM' undeclared (first use in this function)
ea.c:248: warning: implicit declaration of function 'lgetxattr'
ea.c:250: error: 'errno' undeclared (first use in this function)
ea.c: In function 'callback_listxattr':
ea.c:268: error: 'ENOENT' undeclared (first use in this function)
ea.c:271: warning: implicit declaration of function 'llistxattr'
ea.c:286: error: 'errno' undeclared (first use in this function)
ea.c:300: error: 'ERANGE' undeclared (first use in this function)
ea.c: In function 'callback_removexattr':
ea.c:319: error: 'EPERM' undeclared (first use in this function)
ea.c:327: warning: implicit declaration of function 'lremovexattr'
ea.c:330: error: 'errno' undeclared (first use in this function)
ea.c:333: warning: control reaches end of non-void function
make: *** [ea.o] Error 1
```

and LZOLayer_fs: (and I also tried CC=gcc-3.4 and CC=gcc-3.3, too.)
$ make
```
gcc -Wall -ansi -W -std=c99 -g -ggdb -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -c -o ea.o ea.c
ea.c:11:24: error: attr/xattr.h: No such file or directory
ea.c:15:18: error: fuse.h: No such file or directory
ea.c: In function 'callback_setxattr':
ea.c:46: error: 'ENOENT' undeclared (first use in this function)
ea.c:46: error: (Each undeclared identifier is reported only once
ea.c:46: error: for each function it appears in.)
ea.c:65: error: 'EINVAL' undeclared (first use in this function)
ea.c:89: warning: implicit declaration of function 'fuse_get_context'
ea.c:89: warning: assignment makes pointer from integer without a cast
ea.c:90: error: dereferencing pointer to incomplete type
ea.c:90: error: dereferencing pointer to incomplete type
ea.c:91: error: 'EACCES' undeclared (first use in this function)
ea.c:98: error: 'errno' undeclared (first use in this function)
ea.c:111: error: 'EPERM' undeclared (first use in this function)
ea.c:121: warning: implicit declaration of function 'lsetxattr'
ea.c:126: warning: control reaches end of non-void function
ea.c: In function 'callback_getxattr':
ea.c:139: error: 'ENOENT' undeclared (first use in this function)
ea.c:164: error: 'ERANGE' undeclared (first use in this function)
ea.c:213: error: 'ENOMEM' undeclared (first use in this function)
ea.c:248: warning: implicit declaration of function 'lgetxattr'
ea.c:250: error: 'errno' undeclared (first use in this function)
ea.c: In function 'callback_listxattr':
ea.c:268: error: 'ENOENT' undeclared (first use in this function)
ea.c:271: warning: implicit declaration of function 'llistxattr'
ea.c:286: error: 'errno' undeclared (first use in this function)
ea.c:300: error: 'ERANGE' undeclared (first use in this function)
ea.c: In function 'callback_removexattr':
ea.c:319: error: 'EPERM' undeclared (first use in this function)
ea.c:327: warning: implicit declaration of function 'lremovexattr'
ea.c:330: error: 'errno' undeclared (first use in this function)
ea.c:333: warning: control reaches end of non-void function
make: *** [ea.o] Error 1
```

Thanks for help.

---

### Post by lloyd_b on 2007-03-29
You're missing some development headers (Note: you should post this on the forums for the application - ./configure should be configured to check for things like this).

As for "fuse.h" - try installing the package "libfuse-dev"
For "attr/xattr.h", try installing the package "libattr1-dev"

Note: don't be too surprised if once you fix these issues, others pop up.

Lloyd B.

---

### Post by bugmenot_user on 2007-03-30
Thanks for help. I installed libfuse-dev and libattr1-dev. CopyFs had been compiled successfully. But LZOLayer_FS had not. (and I also installed  liblzo-dev)
```
gcc -o lzo_fs LZOlayer_fs.c -g  -Wall -g -D_FILE_OFFSET_BITS=64 -I/usr/include/lzo/ -O2 -s -fomit-frame-pointer -lfuse -lz -llzo2
LZOlayer_fs.c: In function 'LZOlayer_read_block':
LZOlayer_fs.c:87: warning: dereferencing type-punned pointer will break strict-aliasing rules
LZOlayer_fs.c:89: warning: dereferencing type-punned pointer will break strict-aliasing rules
LZOlayer_fs.c: In function 'LZOlayer_packet_sync':
LZOlayer_fs.c:284: warning: dereferencing type-punned pointer will break strict-aliasing rules
LZOlayer_fs.c:288: warning: integer overflow in expression
LZOlayer_fs.c:288: warning: integer overflow in expression
LZOlayer_fs.c: In function 'LZOlayer_truncate':
LZOlayer_fs.c:418: warning: dereferencing type-punned pointer will break strict-aliasing rules
LZOlayer_fs.c:459: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/bin/ld: cannot find -llzo2
collect2: ld returned 1 exit status
make: *** [lzo_fs] Error 1

```

---

### Post by lloyd_b on 2007-03-30
> Thanks for help. I installed libfuse-dev and libattr1-dev. CopyFs had been compiled successfully. But LZOLayer_FS had not. (and I also installed liblzo-dev)

> ```
/usr/bin/ld: cannot find -llzo2
```

This error indicates that it's looking for a library for "lzo2", but can't find it.

It looks like this build requires "lzo2", rather than "lzo1".  Try installing the packages "liblzo2-2" and "liblzo2-dev".

Lloyd B.

---

### Post by bugmenot_user on 2007-03-31
Thanks again. lzo2-2 are not in dapper repos. If I can, I'll compile and package those from edgy sources. Dapper has started to age :D 

> **lloyd_b said:**
> ... (Note: you should post this on the forums for the application - ./configure should be configured to check for things like this)...
 I'll inform the developer.

---

### Post by bugmenot_user on 2007-04-01
I've compiled and packaged liblzo2-2 and liblzo2-dev, I've installed them and I compiled lzo_layerfs successfully. Thanks very much!

---

