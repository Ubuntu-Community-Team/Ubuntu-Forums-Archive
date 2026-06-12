---
title: "Impossible to install exfat-nofuse"
date: 2015-02-20
forum: General Help
---

### Post by ziovelvet on 2015-02-20
Hello, I'm trying to install exfat-nofuse ([https://github.com/dorimanx/exfat-nofuse](https://github.com/dorimanx/exfat-nofuse)) into lubuntu 14.10 with no success.

I have to say I'm not an expert with linux so I literally have no idea what to do.

This is what I get:
```
~/Downloads/exfat-nofuse-master$ make
arch/x86/Makefile:136: CONFIG_X86_X32 enabled but no binutils support
Makefile:652: Cannot use CONFIG_CC_STACKPROTECTOR_REGULAR: -fstack-protector not supported by compiler
scripts/basic/fixdep.c:462:1: fatal error: opening dependency file scripts/basic/.fixdep.d: Permission denied
 }
 ^
compilation terminated.
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make -C /lib/modules/3.16.0-23-generic/build M=/home/ziovelvet/Downloads/exfat-nofuse-master modules
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-23-generic'
  CC [M]  /home/ziovelvet/Downloads/exfat-nofuse-master/exfat_core.o
  CC [M]  /home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.o
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:1329:17: error: ‘generic_file_aio_read’ undeclared here (not in a function)
  .aio_read    = generic_file_aio_read,
                 ^
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:1330:17: error: ‘generic_file_aio_write’ undeclared here (not in a function)
  .aio_write   = generic_file_aio_write,
                 ^
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c: In function ‘exfat_direct_IO’:
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:1584:44: warning: passing argument 4 of ‘blockdev_direct_IO’ from incompatible pointer type
  ret = blockdev_direct_IO(rw, iocb, inode, iov,
                                            ^
In file included from include/linux/pagemap.h:8:0,
                 from /home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:57:
include/linux/fs.h:2512:23: note: expected ‘struct iov_iter *’ but argument is of type ‘const struct iovec *’
 static inline ssize_t blockdev_direct_IO(int rw, struct kiocb *iocb,
                       ^
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:1585:14: warning: passing argument 6 of ‘blockdev_direct_IO’ makes pointer from integer without a cast
      offset, nr_segs, exfat_get_block);
              ^
In file included from include/linux/pagemap.h:8:0,
                 from /home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:57:
include/linux/fs.h:2512:23: note: expected ‘int (*)(struct inode *, sector_t,  struct buffer_head *, int)’ but argument is of type ‘long unsigned int’
 static inline ssize_t blockdev_direct_IO(int rw, struct kiocb *iocb,
                       ^
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:1584:8: error: too many arguments to function ‘blockdev_direct_IO’
  ret = blockdev_direct_IO(rw, iocb, inode, iov,
        ^
In file included from include/linux/pagemap.h:8:0,
                 from /home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:57:
include/linux/fs.h:2512:23: note: declared here
 static inline ssize_t blockdev_direct_IO(int rw, struct kiocb *iocb,
                       ^
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c: At top level:
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:1626:2: warning: initialization from incompatible pointer type
  .direct_IO   = exfat_direct_IO,
  ^
/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.c:1626:2: warning: (near initialization for ‘exfat_aops.direct_IO’)
scripts/Makefile.build:257: recipe for target '/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.o' failed
make[2]: *** [/home/ziovelvet/Downloads/exfat-nofuse-master/exfat_super.o] Error 1
Makefile:1345: recipe for target '_module_/home/ziovelvet/Downloads/exfat-nofuse-master' failed
make[1]: *** [_module_/home/ziovelvet/Downloads/exfat-nofuse-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-23-generic'
Makefile:37: recipe for target 'all' failed
make: *** [all] Error 2
ziovelvet@netbook:~/Downloads/exfat-nofuse-master$ sudo make install
In file included from scripts/kconfig/zconf.tab.c:2537:0:
scripts/kconfig/menu.c: In function ‘get_symbol_str’:
scripts/kconfig/menu.c:590:18: warning: ‘jump’ may be used uninitialized in this function [-Wmaybe-uninitialized]
     jump->offset = strlen(r->s);
                  ^
scripts/kconfig/menu.c:551:19: note: ‘jump’ was declared here
  struct jump_key *jump;
                   ^
rm -f /lib/modules/3.16.4/kernel/fs/exfat/exfat.ko
install -m644 -b -D exfat.ko /lib/modules/3.16.4/kernel/fs/exfat/exfat.ko
depmod -aq
```

Please help me!

---

### Post by kerry_s on 2015-02-20
that says for android arm linux.

if your trying to install in lubuntu it's already in the repo's
sudo apt-get install exfat-fuse exfat-utils

---

### Post by ziovelvet on 2015-02-23
Thank you kerry_s, I've solved it! I wasn't able to load it to the kernel though.

---

### Post by wzhy90 on 2015-03-04
> **ziovelvet said:**
> Thank you kerry_s, I've solved it! I wasn't able to load it to the kernel though.

Please repull your codes. I have fixed installing the modules to the wrong patch. If you can compile it and now you can load it.

---

