---
title: "Is there something I should know about compiling older kernels?"
date: 2005-09-27
forum: General Help
---

### Post by starkruzr on 2005-09-27
I'm trying to compile 2.4.19.

make mrproper

No problems.

make menuconfig

No problems.

make dep

No problems.

make bzImage
```

jdeange2@rts-testbed:/usr/src/linux-2.4.19$ make bzImage
gcc -D__KERNEL__ -I/usr/src/linux-2.4.19/include -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i586   -DKBUILD_BASENAME=main -c -o init/main.o init/main.c
In file included from /usr/src/linux-2.4.19/include/linux/prefetch.h:13,
                 from /usr/src/linux-2.4.19/include/linux/list.h:6,
                 from /usr/src/linux-2.4.19/include/linux/wait.h:14,
                 from /usr/src/linux-2.4.19/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.19/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.19/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.19/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.19/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.19/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.19/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.19/include/asm/processor.h:74: error: array type has incomplete element type
In file included from /usr/src/linux-2.4.19/include/linux/fs.h:201,
                 from /usr/src/linux-2.4.19/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.19/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.19/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.19/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.19/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.19/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.19/include/asm/byteorder.h:14: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.19/include/asm/byteorder.h:28: warning: type qualifiers ignored on function return type
In file included from /usr/src/linux-2.4.19/include/linux/byteorder/little_endian.h:11,
                 from /usr/src/linux-2.4.19/include/asm/byteorder.h:45,
                 from /usr/src/linux-2.4.19/include/linux/fs.h:201,
                 from /usr/src/linux-2.4.19/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.19/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.19/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.19/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.19/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.19/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.19/include/linux/byteorder/swab.h:132: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.19/include/linux/byteorder/swab.h:145: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.19/include/linux/byteorder/swab.h:159: warning: type qualifiers ignored on function return type
In file included from /usr/src/linux-2.4.19/include/linux/unistd.h:9,
                 from init/main.c:17:
/usr/src/linux-2.4.19/include/asm/unistd.h:365: warning: conflicting types for built-in function ‘_exit’
make: *** [init/main.o] Error 1
```

I'm probably doing something really obviously stupid, but I don't know what it is.

---

### Post by az on 2005-09-28
What version of gcc are you using?

Also, you will need to change the init sripts since the old kernel will not support Udev.  You need to put skeleton device nodes in /dev and not bury them by mounting another /dev directory over them.  There may be other things, too, but I have not been successful.

---

