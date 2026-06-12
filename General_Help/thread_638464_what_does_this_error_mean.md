---
title: "what does this error mean?"
date: 2007-12-12
forum: General Help
---

### Post by Dr.Suse on 2007-12-12
what does this error mean and how do i fix it??

```
cobin@bluth:~$ sudo airmon-ng


Interface       Chipset         Driver

*** glibc detected *** grep: free(): invalid pointer: 0x08076a6c ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7eb0d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7eb4800]
grep[0x8052100]
grep[0x805a208]
grep[0x804c228]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7e5d050]
grep[0x80499e1]
======= Memory map: ========
08048000-0805f000 r-xp 00000000 03:01 491562     /bin/grep
0805f000-08060000 rw-p 00017000 03:01 491562     /bin/grep
08060000-08081000 rw-p 08060000 00:00 0          [heap]
b7c00000-b7c21000 rw-p b7c00000 00:00 0 
b7c21000-b7d00000 ---p b7c21000 00:00 0 
b7d0b000-b7d15000 r-xp 00000000 03:01 950339     /lib/libgcc_s.so.1
b7d15000-b7d16000 rw-p 0000a000 03:01 950339     /lib/libgcc_s.so.1
b7d26000-b7d65000 r--p 00000000 03:01 3425459    /usr/lib/locale/en_US.utf8/LC_CTYPE
b7d65000-b7d66000 r--p 00000000 03:01 3425464    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7d66000-b7e46000 r--p 00000000 03:01 3425458    /usr/lib/locale/en_US.utf8/LC_COLLATE
b7e46000-b7e47000 rw-p b7e46000 00:00 0 
b7e47000-b7f8b000 r-xp 00000000 03:01 984011     /lib/tls/i686/cmov/libc-2.6.1.so
b7f8b000-b7f8c000 r--p 00143000 03:01 984011     /lib/tls/i686/cmov/libc-2.6.1.so
b7f8c000-b7f8e000 rw-p 00144000 03:01 984011     /lib/tls/i686/cmov/libc-2.6.1.so
b7f8e000-b7f91000 rw-p b7f8e000 00:00 0 
b7f91000-b7f92000 r--p 00000000 03:01 3425467    /usr/lib/locale/en_US.utf8/LC_TIME
b7f92000-b7f93000 r--p 00000000 03:01 3425462    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f93000-b7f94000 r--p 00000000 03:01 3440684    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f94000-b7f95000 r--p 00000000 03:01 3425465    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f95000-b7f96000 r--p 00000000 03:01 3425463    /usr/lib/locale/en_US.utf8/LC_NAME
b7f96000-b7f97000 r--p 00000000 03:01 3425457    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f97000-b7f98000 r--p 00000000 03:01 3425466    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f98000-b7f99000 r--p 00000000 03:01 3425461    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f99000-b7fa0000 r--s 00000000 03:01 3392184    /usr/lib/gconv/gconv-modules.cache
b7fa0000-b7fa1000 r--p 00000000 03:01 3425460    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fa1000-b7fa3000 rw-p b7fa1000 00:00 0 
b7fa3000-b7fbd000 r-xp 00000000 03:01 950920     /lib/ld-2.6.1.so
b7fbd000-b7fbf000 rw-p 00019000 03:01 950920     /lib/ld-2.6.1.so
bf828000-bf83e000 rw-p bf828000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
Segmentation fault (core dumped)
*** glibc detected *** grep: free(): invalid pointer: 0x0807687c ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e36d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e3a800]
grep[0x8052100]
grep[0x8059a74]
grep[0x804c228]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7de3050]
grep[0x80499e1]
======= Memory map: ========
08048000-0805f000 r-xp 00000000 03:01 491562     /bin/grep
0805f000-08060000 rw-p 00017000 03:01 491562     /bin/grep
08060000-08081000 rw-p 08060000 00:00 0          [heap]
b7b00000-b7b21000 rw-p b7b00000 00:00 0 
b7b21000-b7c00000 ---p b7b21000 00:00 0 
b7c91000-b7c9b000 r-xp 00000000 03:01 950339     /lib/libgcc_s.so.1
b7c9b000-b7c9c000 rw-p 0000a000 03:01 950339     /lib/libgcc_s.so.1
b7cac000-b7ceb000 r--p 00000000 03:01 3425459    /usr/lib/locale/en_US.utf8/LC_CTYPE
b7ceb000-b7cec000 r--p 00000000 03:01 3425464    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7cec000-b7dcc000 r--p 00000000 03:01 3425458    /usr/lib/locale/en_US.utf8/LC_COLLATE
b7dcc000-b7dcd000 rw-p b7dcc000 00:00 0 
b7dcd000-b7f11000 r-xp 00000000 03:01 984011     /lib/tls/i686/cmov/libc-2.6.1.so
b7f11000-b7f12000 r--p 00143000 03:01 984011     /lib/tls/i686/cmov/libc-2.6.1.so
b7f12000-b7f14000 rw-p 00144000 03:01 984011     /lib/tls/i686/cmov/libc-2.6.1.so
b7f14000-b7f17000 rw-p b7f14000 00:00 0 
b7f17000-b7f18000 r--p 00000000 03:01 3425467    /usr/lib/locale/en_US.utf8/LC_TIME
b7f18000-b7f19000 r--p 00000000 03:01 3425462    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f19000-b7f1a000 r--p 00000000 03:01 3440684    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f1a000-b7f1b000 r--p 00000000 03:01 3425465    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f1b000-b7f1c000 r--p 00000000 03:01 3425463    /usr/lib/locale/en_US.utf8/LC_NAME
b7f1c000-b7f1d000 r--p 00000000 03:01 3425457    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f1d000-b7f1e000 r--p 00000000 03:01 3425466    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f1e000-b7f1f000 r--p 00000000 03:01 3425461    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f1f000-b7f26000 r--s 00000000 03:01 3392184    /usr/lib/gconv/gconv-modules.cache
b7f26000-b7f27000 r--p 00000000 03:01 3425460    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f27000-b7f29000 rw-p b7f27000 00:00 0 
b7f29000-b7f43000 r-xp 00000000 03:01 950920     /lib/ld-2.6.1.so
b7f43000-b7f45000 rw-p 00019000 03:01 950920     /lib/ld-2.6.1.so
bf93a000-bf950000 rw-p bf93a000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

cobin@bluth:~$ 

```

---

### Post by gaten on 2007-12-13
That's a problem with the executable, looks like it tried to free some memory that wasn't in use. Did you compile this yourself? Try reinstalling it, or running it with some flags.

---

### Post by ubutufan on 2007-12-13
The correct syntax is
sudo airmon-ng eth1 if your wireless card has been assigned  as eth1.
Type ifconfig on terminal to see what is assigned to your wireless interface

---

