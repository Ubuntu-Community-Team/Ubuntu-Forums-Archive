---
title: "Voyager 105 not working - synch failed plus usb alt config submenu"
date: 2008-04-25
forum: General Help
---

### Post by geeforce on 2008-04-25
Hi there folks. Hi followed Welsh-Buds how to to get the modem running under Ubuntu 8.04.

However, there are some points he didn´t mention. Well there´s this usb alt config submenu. Dunno what I need to enter there. It says USB alt and USB Alt Sync with choices from 0-5. I´ve absolutely no idea what went wrong. I enclosed a list with the code when the modem tries to connect.

So here a list of my modem when it tries to connect. Any help is much appreciated.

```
[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

*** glibc detected *** /usr/bin/eciadsl-synch: double free or corruption (fasttop): 0x0804f158 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e99a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e9d4f0]
/usr/bin/eciadsl-synch[0x804b003]
/usr/bin/eciadsl-synch[0x804a552]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7e44450]
/usr/bin/eciadsl-synch[0x8048e61]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:05 2670324    /usr/bin/eciadsl-synch
0804e000-0804f000 rw-p 00006000 08:05 2670324    /usr/bin/eciadsl-synch
0804f000-08070000 rw-p 0804f000 00:00 0          [heap]
b6d00000-b6d21000 rw-p b6d00000 00:00 0 
b6d21000-b6e00000 ---p b6d21000 00:00 0 
b6e14000-b6e1e000 r-xp 00000000 08:05 2293776    /lib/libgcc_s.so.1
b6e1e000-b6e1f000 rw-p 0000a000 08:05 2293776    /lib/libgcc_s.so.1
b6e2a000-b6e2b000 ---p b6e2a000 00:00 0 
b6e2b000-b762b000 rw-p b6e2b000 00:00 0 
b762b000-b762c000 ---p b762b000 00:00 0 
b762c000-b7e2e000 rw-p b762c000 00:00 0 
b7e2e000-b7f77000 r-xp 00000000 08:05 2293914    /lib/tls/i686/cmov/libc-2.7.so
b7f77000-b7f78000 r--p 00149000 08:05 2293914    /lib/tls/i686/cmov/libc-2.7.so
b7f78000-b7f7a000 rw-p 0014a000 08:05 2293914    /lib/tls/i686/cmov/libc-2.7.so
b7f7a000-b7f7d000 rw-p b7f7a000 00:00 0 
b7f7d000-b7f91000 r-xp 00000000 08:05 2293930    /lib/tls/i686/cmov/libpthread-2.7.so
b7f91000-b7f93000 rw-p 00013000 08:05 2293930    /lib/tls/i686/cmov/libpthread-2.7.so
b7f93000-b7f95000 rw-p b7f93000 00:00 0 
b7f9d000-b7f9e000 rw-p b7f9d000 00:00 0 
b7f9f000-b7fa2000 rw-p b7f9f000 00:00 0 
b7fa2000-b7fa3000 r-xp b7fa2000 00:00 0          [vdso]
b7fa3000-b7fbd000 r-xp 00000000 08:05 2293777    /lib/ld-2.7.so
b7fbd000-b7fbf000 rw-p 00019000 08:05 2293777    /lib/ld-2.7.so
bfa70000-bfa85000 rw-p bffeb000 00:00 0          [stack]
 Please Wait.. Synchronisation in progress [-]/usr/bin/eciadsl-start: line 517:  7111 Aborted                 "$BIN_DIR/eciadsl-synch" $synch_options
ERROR: failed to get synchronization

```

Could someone please help me?

---

