---
title: "Iscsi target - broken?"
date: 2017-01-04
forum: General Help
---

### Post by ilemur on 2017-01-04
After the latest update started seeing errors that iscsi_target module not found. Well than it's now a Linux 4.4.0-57-generic #78~14.04.1-Ubuntu SMP

Did this
```
[COLOR=#000000][FONT=&quot] sudo apt-get install --reinstall iscsitarget-dkms[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Building dependency tree[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Need to get 0 B/63.9 kB of archives.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]After this operation, 0 B of additional disk space will be used.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot](Reading database ... 345455 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Preparing to unpack .../iscsitarget-dkms_1.4.20.3+svn499-0ubuntu2.1_all.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error! There are no instances of module: iscsitarget[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]1.4.20.3+svn499 located in the DKMS tree.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Unpacking iscsitarget-dkms (1.4.20.3+svn499-0ubuntu2.1) over (1.4.20.3+svn499-0ubuntu2.1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Setting up iscsitarget-dkms (1.4.20.3+svn499-0ubuntu2.1) ...[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Creating symlink /var/lib/dkms/iscsitarget/1.4.20.3+svn499/source ->[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]                 /usr/src/iscsitarget-1.4.20.3+svn499[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]DKMS: add completed.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Kernel preparation unnecessary for this kernel.  Skipping...[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Building module:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]cleaning build area....[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]make KERNELRELEASE=4.4.0-57-generic -C /lib/modules/4.4.0-57-generic/build M=/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build........(bad exit status: 2)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/iscsitarget-dkms.0.crash'[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error! Bad return status for module build on kernel: 4.4.0-57-generic (x86_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Consult /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/make.log for more information[/FONT][/COLOR]
```

And the make.log

```
make: Entering directory `/usr/src/linux-headers-4.4.0-57-generic'
  LD      /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/built-in.o
  LD      /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/built-in.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/tio.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/iscsi.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/nthread.o
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/nthread.c: In function ‘forward_iov’:
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/nthread.c:94:6: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
  iov = msg->msg_iter.iov;
      ^
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/nthread.c: In function ‘close_conn’:
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/nthread.c:676:32: warning: assignment from incompatible pointer type [enabled by default]
  conn->sock->sk->sk_data_ready = target->nthread_info.old_data_ready;
                                ^
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/nthread.c: In function ‘do_recv’:
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/nthread.c:154:1: warning: the frame size of 1128 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/wthread.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/config.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/digest.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/conn.o
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/conn.c: In function ‘iet_socket_bind’:
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/conn.c:137:38: warning: assignment from incompatible pointer type [enabled by default]
  target->nthread_info.old_data_ready = conn->sock->sk->sk_data_ready;
                                      ^
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/conn.c:138:32: warning: assignment from incompatible pointer type [enabled by default]
  conn->sock->sk->sk_data_ready = iet_data_ready;
                                ^
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/session.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/target.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/volume.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/iotype.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/file-io.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/null-io.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/target_disk.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/event.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/param.o
  CC [M]  /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.o
In file included from include/linux/bitops.h:36:0,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:17,
                 from include/linux/blkdev.h:4,
                 from /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:13:
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c: In function ‘blockio_bio_endio’:
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:36:19: error: ‘BIO_UPTODATE’ undeclared (first use in this function)
  error = test_bit(BIO_UPTODATE, &bio->bi_flags) ? error : -EIO;
                   ^
./arch/x86/include/asm/bitops.h:336:25: note: in definition of macro ‘test_bit’
  (__builtin_constant_p((nr))  \
                         ^
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:36:19: note: each undeclared identifier is reported only once for each function it appears in
  error = test_bit(BIO_UPTODATE, &bio->bi_flags) ? error : -EIO;
                   ^
./arch/x86/include/asm/bitops.h:336:25: note: in definition of macro ‘test_bit’
  (__builtin_constant_p((nr))  \
                         ^
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:36:2: warning: passing argument 2 of ‘constant_test_bit’ from incompatible pointer type [enabled by default]
  error = test_bit(BIO_UPTODATE, &bio->bi_flags) ? error : -EIO;
  ^
In file included from include/linux/bitops.h:36:0,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:17,
                 from include/linux/blkdev.h:4,
                 from /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:13:
./arch/x86/include/asm/bitops.h:308:28: note: expected ‘const volatile long unsigned int *’ but argument is of type ‘unsigned int *’
 static __always_inline int constant_test_bit(long nr, const volatile unsigned long *addr)
                            ^
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:36:2: warning: passing argument 2 of ‘variable_test_bit’ from incompatible pointer type [enabled by default]
  error = test_bit(BIO_UPTODATE, &bio->bi_flags) ? error : -EIO;
  ^
In file included from include/linux/bitops.h:36:0,
                 from include/linux/kernel.h:10,
                 from include/linux/sched.h:17,
                 from include/linux/blkdev.h:4,
                 from /var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:13:
./arch/x86/include/asm/bitops.h:314:19: note: expected ‘const volatile long unsigned int *’ but argument is of type ‘unsigned int *’
 static inline int variable_test_bit(long nr, volatile const unsigned long *addr)
                   ^
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c: In function ‘blockio_make_request’:
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:71:3: error: implicit declaration of function ‘bio_get_nr_vecs’ [-Werror=implicit-function-declaration]
   max_pages = bio_get_nr_vecs(bio_data->bdev);
   ^
/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.c:92:18: warning: assignment from incompatible pointer type [enabled by default]
   bio->bi_end_io = blockio_bio_endio;
                  ^
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel/block-io.o] Error 1
make[1]: *** [/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build/kernel] Error 2
make: *** [_module_/var/lib/dkms/iscsitarget/1.4.20.3+svn499/build] Error 2
make: Leaving directory `/usr/src/linux-headers-4.4.0-57-generic'
&#1057;&#1086;&#1086;&#1073;&#1097;&#1080;&#1090;&#1100; &#1084;&#1086;&#1076;&#1077;&#1088;&#1072;&#1090;&#1086;&#1088;&#1091;    &#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1090;&#1100; &#1089;&#1086;&#1086;&#1073;&#1097;&#1077;&#1085;&#1080;&#1077;



```

---

### Post by wildmanne39 on 2017-01-04
*Thread moved to **General Help**.*

---

### Post by wildmanne39 on 2017-01-04
I am not an expert on this but it looks like you do not have the required packages installed to build the package, please do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
watch for error, when done try to install the package again,
Thanks

---

