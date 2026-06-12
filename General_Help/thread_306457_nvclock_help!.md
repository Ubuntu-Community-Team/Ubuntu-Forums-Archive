---
title: "nvclock help!"
date: 2006-11-25
forum: General Help
---

### Post by umanzor on 2006-11-25
Hi, I get the following while running nvclock with any option:

```
umanzor@home:~$ nvclock -c
*** glibc detected *** nvclock: malloc(): memory corruption: 0x0805d160 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d851cd]
/lib/tls/i686/cmov/libc.so.6(calloc+0x8e)[0xb7d8653e]
nvclock[0x804d137]
nvclock[0x804dfad]
nvclock[0x804d700]
nvclock[0x8053827]
nvclock[0x804a720]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7d338cc]
nvclock[0x8048ff1]
======= Memory map: ========
08048000-0805c000 r-xp 00000000 03:05 447373     /usr/bin/nvclock
0805c000-0805d000 rw-p 00013000 03:05 447373     /usr/bin/nvclock
0805d000-0807e000 rw-p 0805d000 00:00 0          [heap]
b7b00000-b7b21000 rw-p b7b00000 00:00 0 
b7b21000-b7c00000 ---p b7b21000 00:00 0 
b7cc6000-b7cd0000 r-xp 00000000 03:05 97987      /lib/libgcc_s.so.1
b7cd0000-b7cd1000 rw-p 00009000 03:05 97987      /lib/libgcc_s.so.1
b7ce0000-b7cf0000 r--s 00000000 03:05 1013349    /home/umanzor/.nvclock/bios0.rom
b7cf0000-b7d00000 rw-s e0300000 00:0d 9103       /dev/nvidia0
b7d00000-b7d10000 rw-s e0000000 00:0d 9103       /dev/nvidia0
b7d10000-b7d11000 rw-p b7d10000 00:00 0 
b7d11000-b7d13000 r-xp 00000000 03:05 101007     /lib/tls/i686/cmov/libdl-2.4.so
b7d13000-b7d15000 rw-p 00001000 03:05 101007     /lib/tls/i686/cmov/libdl-2.4.so
b7d15000-b7d19000 r-xp 00000000 03:05 442147     /usr/lib/libXdmcp.so.6.0.0
b7d19000-b7d1a000 rw-p 00003000 03:05 442147     /usr/lib/libXdmcp.so.6.0.0
b7d1a000-b7d1c000 r-xp 00000000 03:05 442138     /usr/lib/libXau.so.6.0.0
b7d1c000-b7d1d000 rw-p 00001000 03:05 442138     /usr/lib/libXau.so.6.0.0
b7d1d000-b7d1e000 rw-p b7d1d000 00:00 0 
b7d1e000-b7e4b000 r-xp 00000000 03:05 101001     /lib/tls/i686/cmov/libc-2.4.so
b7e4b000-b7e4d000 r--p 0012c000 03:05 101001     /lib/tls/i686/cmov/libc-2.4.so
b7e4d000-b7e4f000 rw-p 0012e000 03:05 101001     /lib/tls/i686/cmov/libc-2.4.so
b7e4f000-b7e52000 rw-p b7e4f000 00:00 0 
b7e52000-b7f18000 r-xp 00000000 03:05 442132     /usr/lib/libX11.so.6.2.0
b7f18000-b7f1b000 rw-p 000c5000 03:05 442132     /usr/lib/libX11.so.6.2.0
b7f1b000-b7f27000 r-xp 00000000 03:05 442151     /usr/lib/libXext.so.6.4.0
b7f27000-b7f28000 rw-p 0000c000 03:05 442151     /usr/lib/libXext.so.6.4.0
b7f31000-b7f33000 rw-s e0680000 00:0d 9103       /dev/nvidia0
b7f33000-b7f35000 rw-s e0601000 00:0d 9103       /dev/nvidia0
b7f35000-b7f36000 rw-s e0100000 00:0d 9103       /dev/nvidia0
b7f36000-b7f37000 rw-s e0101000 00:0d 9103       /dev/nvidia0
b7f37000-b7f39000 rw-p b7f37000 00:00 0 
b7f39000-b7f52000 r-xp 00000000 03:05 97942      /lib/ld-2.4.so
b7f52000-b7f54000 rw-p 00018000 03:05 97942      /lib/ld-2.4.so
bfabf000-bfad4000 rw-p bfabf000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Tried nvclock_gtk as well, same problem. Any ideas?

---

