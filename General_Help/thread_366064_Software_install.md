---
title: "Software install"
date: 2007-02-20
forum: General Help
---

### Post by yme on 2007-02-20
I'm trying to install a programme, Secure Delete, which is not available via the Add/Remove programmes options. I've only had a couple of experiences doing this with Fedora3.

I moved the downloaded tarball to usr/local and then:

yme@yme:/usr/local$ sudo tar zxvpf secure_delete-3.1.tar.gz
secure_delete-3.1/
secure_delete-3.1/CHANGES
secure_delete-3.1/FILES
secure_delete-3.1/Makefile
secure_delete-3.1/README
secure_delete-3.1/TODO
secure_delete-3.1/config.h
secure_delete-3.1/rm-fileutil-3.x.diff
secure_delete-3.1/sdel-lib.c
secure_delete-3.1/sdel-lib.h
secure_delete-3.1/sdel-mod.c
secure_delete-3.1/sdel.h
secure_delete-3.1/secure_delete.doc
secure_delete-3.1/sfill.1
secure_delete-3.1/sfill.c
secure_delete-3.1/smem.1
secure_delete-3.1/smem.c
secure_delete-3.1/srm.1
secure_delete-3.1/srm.c
secure_delete-3.1/sswap.1
secure_delete-3.1/sswap.c
secure_delete-3.1/the_cleaner.sh
secure_delete-3.1/usenix6-gutmann.doc
secure_delete-3.1/rm-fileutil-4.1.diff
secure_delete-3.1/configure

So far so good. Then I try:

yme@yme:/usr/local/secure_delete-3.1$ ./configure
Just run "make" and "make install"

Lovely! Then:

yme@yme:/usr/local/secure_delete-3.1$ make
bash: make: command not found

What is wrong? For the record, I did ls and got:

yme@yme:/usr/local/secure_delete-3.1$ ls
CHANGES    rm-fileutil-3.x.diff  secure_delete.doc  srm.c
config.h   rm-fileutil-4.1.diff  sfill.1            sswap.1
configure  sdel.h                sfill.c            sswap.c
FILES      sdel-lib.c            smem.1             the_cleaner.sh
Makefile   sdel-lib.h            smem.c             TODO
README     sdel-mod.c            srm.1              usenix6-gutmann.doc

---

### Post by llamakc on 2007-02-20
You need to install the software packages that enable you to build.

sudo apt-get install build-essential

---

### Post by yme on 2007-02-20
Cheers! I did that, all seemed OK and tried again first typing just make, then sudo make. Neither worked:

yme@yme:/usr/local/secure_delete-3.1$ make
gcc -O2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -c sdel-lib.c
sdel-lib.c: In function ‘sdel_overwrite’:
sdel-lib.c:173: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
sdel-lib.c:175: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
sdel-lib.c:200: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
sdel-lib.c:209: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
Assembler messages:
FATAL: can't create sdel-lib.o: Permission denied
make: *** [sdel-lib.o] Error 1
yme@yme:/usr/local/secure_delete-3.1$ sudo make
gcc -O2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -c sdel-lib.c
sdel-lib.c: In function ‘sdel_overwrite’:
sdel-lib.c:173: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
sdel-lib.c:175: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
sdel-lib.c:200: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
sdel-lib.c:209: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
gcc -O2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o srm srm.c sdel-lib.o
strip srm
gcc -O2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o sfill sfill.c sdel-lib.o
strip sfill
gcc -O2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o sswap sswap.c sdel-lib.o
strip sswap
gcc -O2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o smem smem.c sdel-lib.o
smem.c: In function ‘smash_it’:
smem.c:122: warning: pointer targets in passing argument 1 of ‘__sdel_fill_buf’ differ in signedness
strip smem
gcc -O2 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D__KERNEL__ -DMODULE -fomit-frame-pointer -fno-strict-aliasing -pipe -mpreferred-stack-boundary=2  -I/lib/modules/`uname -r`/build/include -c sdel-mod.c
In file included from sdel-mod.c:8:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from sdel-mod.c:16:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from sdel-mod.c:16:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from sdel-mod.c:16:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
sdel-mod.c:17:24: error: linux/slab.h: No such file or directory
sdel-mod.c:21:25: error: asm/uaccess.h: No such file or directory
sdel-mod.c:22:25: error: asm/smplock.h: No such file or directory
sdel-mod.c:33: warning: ‘struct stat’ declared inside parameter list
sdel-mod.c:33: warning: its scope is only this definition or declaration, which is probably not what you want
sdel-mod.c:34: warning: ‘struct stat’ declared inside parameter list
sdel-mod.c: In function ‘__sdel_random_filename’:
sdel-mod.c:82: warning: incompatible implicit declaration of built-in function ‘strlen’
sdel-mod.c: In function ‘sdel_unlink’:
sdel-mod.c:100: warning: incompatible implicit declaration of built-in function ‘strlen’
sdel-mod.c:103: error: storage size of ‘filestat’ isn’t known
sdel-mod.c:106: warning: incompatible implicit declaration of built-in function ‘strcpy’
sdel-mod.c:115: error: ‘current’ undeclared (first use in this function)
sdel-mod.c:115: error: (Each undeclared identifier is reported only once
sdel-mod.c:115: error: for each function it appears in.)
sdel-mod.c:117: error: ‘KERN_DEBUG’ undeclared (first use in this function)
sdel-mod.c:117: error: syntax error before string constant
sdel-mod.c:124: error: syntax error before string constant
sdel-mod.c:128: error: syntax error before string constant
sdel-mod.c:134: error: syntax error before string constant
sdel-mod.c: At top level:
sdel-mod.c:169: warning: ‘struct stat’ declared inside parameter list
sdel-mod.c:169: error: parameter 3 (‘kl_filestat’) has incomplete type
sdel-mod.c: In function ‘smash_it’:
sdel-mod.c:173: error: storage size of ‘kl_controlstat’ isn’t known
sdel-mod.c:197: error: ‘O_RDWR’ undeclared (first use in this function)
sdel-mod.c:198: error: ‘KERN_DEBUG’ undeclared (first use in this function)
sdel-mod.c:198: error: syntax error before string constant
sdel-mod.c:204: error: ‘current’ undeclared (first use in this function)
sdel-mod.c:205: error: invalid application of ‘sizeof’ to incomplete type ‘struct stat’
sdel-mod.c:206: error: syntax error before string constant
sdel-mod.c:214: warning: passing argument 2 of ‘fstat_orig’ from incompatible pointer type
sdel-mod.c:215: error: syntax error before string constant
sdel-mod.c:222: error: invalid application of ‘sizeof’ to incomplete type ‘struct stat’
sdel-mod.c:228: error: syntax error before string constant
sdel-mod.c:241: warning: pointer targets in passing argument 1 of ‘fill_buf’ differ in signedness
sdel-mod.c:245: error: syntax error before string constant
sdel-mod.c:255: error: syntax error before string constant
sdel-mod.c:267: error: syntax error before string constant
sdel-mod.c:276: warning: pointer targets in passing argument 1 of ‘fill_buf’ differ in signedness
sdel-mod.c:302: error: ‘O_WRONLY’ undeclared (first use in this function)
sdel-mod.c:302: error: ‘O_TRUNC’ undeclared (first use in this function)
sdel-mod.c: In function ‘wipefile’:
sdel-mod.c:314: error: storage size of ‘kl_filestat’ isn’t known
sdel-mod.c:324: warning: assignment makes pointer from integer without a cast
sdel-mod.c:328: error: ‘KERN_DEBUG’ undeclared (first use in this function)
sdel-mod.c:328: error: syntax error before string constant
sdel-mod.c:335: warning: incompatible implicit declaration of built-in function ‘strlen’
sdel-mod.c:338: error: ‘current’ undeclared (first use in this function)
sdel-mod.c:339: error: invalid application of ‘sizeof’ to incomplete type ‘struct stat’
sdel-mod.c:342: warning: passing argument 2 of ‘lstat_orig’ from incompatible pointer type
sdel-mod.c:350: error: invalid application of ‘sizeof’ to incomplete type ‘struct stat’
sdel-mod.c:357: error: type of formal parameter 3 is incomplete
sdel-mod.c:374: error: syntax error before string constant
sdel-mod.c: In function ‘init_module’:
sdel-mod.c:389: error: ‘KERN_INFO’ undeclared (first use in this function)
sdel-mod.c:389: error: syntax error before string constant
sdel-mod.c: In function ‘cleanup_module’:
sdel-mod.c:418: error: ‘KERN_INFO’ undeclared (first use in this function)
sdel-mod.c:418: error: syntax error before string constant
make: *** [sdel-mod.o] Error 1

---

### Post by llamakc on 2007-02-20
Make is working just fine. 

Looks like you need to read:

```

/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/)"
```


which is right here:

[http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/FAQ](http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/FAQ)

By the way, secure-delete is in Fiesty Fawn.

[http://packages.ubuntu.com/feisty/utils/secure-delete](http://packages.ubuntu.com/feisty/utils/secure-delete)

If you're not using Fiesty, what is wrong with "shred"?

---

### Post by yme on 2007-02-20
Double posting

---

### Post by yme on 2007-02-20
> **llamakc said:**
>  Looks like you need to read:

[http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/FAQ](http://ep09.pld-linux.org/~mmazur/linux-libc-headers/doc/FAQ)

By the way, secure-delete is in Fiesty Fawn.

[http://packages.ubuntu.com/feisty/utils/secure-delete](http://packages.ubuntu.com/feisty/utils/secure-delete)

If you're not using Fiesty, what is wrong with "shred"?

I read it which is not to say that I understood it.

Secure Delete is supposed to have several advantages over Shred in that it overwrite blank space as well as securely delete individual documents.

But both are supposed not to work on ext3 as it is a journaling file system ...

---

### Post by llamakc on 2007-02-20
So, are you using ext3? If you're using ext3 and you are aware it doesn't work, why are you trying to install it?

---

### Post by yme on 2007-02-23
> **llamakc said:**
> So, are you using ext3? If you're using ext3 and you are aware it doesn't work, why are you trying to install it?

I'm thinking that while the srm won't work, sfill will still overwrite blank space without problems.

---

