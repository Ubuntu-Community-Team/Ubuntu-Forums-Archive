---
title: "The search results may be out of date or invalid.  Do you want to disable the quick s"
date: 2007-08-24
forum: General Help
---

### Post by Super TWiT on 2007-08-24
When I searched for a file on my computer  I got an error dialog saying: The search results may be out of date or invalid.  Do you want to disable the quick search?  When running the search tool in the terminal it says:```
*** glibc detected *** /usr/bin/locate: double free or corruption (fasttop): 0x08052850 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e137cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e16e30]
/usr/bin/locate[0x804b149]
/usr/bin/locate[0x804af63]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7dc1ebc]
/usr/bin/locate[0x80492e1]
======= Memory map: ========
08048000-08050000 r-xp 00000000 08:04 767995     /usr/bin/slocate
08050000-08051000 rw-p 00007000 08:04 767995     /usr/bin/slocate
08051000-08072000 rw-p 08051000 00:00 0          [heap]
b7c00000-b7c21000 rw-p b7c00000 00:00 0 
b7c21000-b7d00000 ---p b7c21000 00:00 0 
b7d76000-b7d7f000 r-xp 00000000 08:04 6611       /lib/tls/i686/cmov/libnss_files-2.5.so
b7d7f000-b7d81000 rw-p 00008000 08:04 6611       /lib/tls/i686/cmov/libnss_files-2.5.so
b7d81000-b7d89000 r-xp 00000000 08:04 6615       /lib/tls/i686/cmov/libnss_nis-2.5.so
b7d89000-b7d8b000 rw-p 00007000 08:04 6615       /lib/tls/i686/cmov/libnss_nis-2.5.so
b7d8b000-b7d9e000 r-xp 00000000 08:04 6605       /lib/tls/i686/cmov/libnsl-2.5.so
b7d9e000-b7da0000 rw-p 00012000 08:04 6605       /lib/tls/i686/cmov/libnsl-2.5.so
b7da0000-b7da2000 rw-p b7da0000 00:00 0 
b7da2000-b7da9000 r-xp 00000000 08:04 6607       /lib/tls/i686/cmov/libnss_compat-2.5.so
b7da9000-b7dab000 rw-p 00006000 08:04 6607       /lib/tls/i686/cmov/libnss_compat-2.5.so
b7dab000-b7dac000 rw-p b7dab000 00:00 0 
b7dac000-b7ee7000 r-xp 00000000 08:04 6594       /lib/tls/i686/cmov/libc-2.5.so
b7ee7000-b7ee8000 r--p 0013b000 08:04 6594       /lib/tls/i686/cmov/libc-2.5.so
b7ee8000-b7eea000 rw-p 0013c000 08:04 6594       /lib/tls/i686/cmov/libc-2.5.so
b7eea000-b7eed000 rw-p b7eea000 00:00 0 
b7ef9000-b7f04000 r-xp 00000000 08:04 3079       /lib/libgcc_s.so.1
b7f04000-b7f05000 rw-p 0000a000 08:04 3079       /lib/libgcc_s.so.1
b7f05000-b7f08000 rw-p b7f05000 00:00 0 
b7f08000-b7f21000 r-xp 00000000 08:04 3038       /lib/ld-2.5.so
b7f21000-b7f23000 rw-p 00019000 08:04 3038       /lib/ld-2.5.so
bf80c000-bf822000 rw-p bf80c000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

``` Does anyone have any idea how to fix this?

---

### Post by Browser_ice on 2008-03-27
I have just gotten the same problem. The search worked ok until I decided to do a search from the FileSystem folder.

Last time I updated was yesterday. I always update and I have 7.10.

What is causing this problem ???

---

