---
title: "Pidgin messenger crash"
date: 2014-03-26
forum: General Help
---

### Post by wouter.inspired on 2014-03-26
Hi folks,

Since a few weeks I've been running a whatsapp protocol through Pidgin messenger. The first week there were no troubles at all.  (except that I couldn't chat with people on android, but I've found a workaround for that -> invite them in a 'private'  group chat)

But now all of a sudden Pidgin started closing itself directly after logging on.  After a re installation this problem seemed to have been solved, but it only mitigated.. Now Pidgin closes after about a minute or 2...

I've seen a few topics on this, but not really a solution..  Anybody got any further?
Please find below the error log copied from the terminal when I was waiting for Pidgin to crash.

Many thanks in advance!



Error log:

*** Error in `pidgin': munmap_chunk(): invalid pointer: 0xb81deb00 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x767c2)[0xb69077c2]
/lib/i386-linux-gnu/libc.so.6(+0x76e85)[0xb6907e85]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_free+0x20)[0xb6c245d0]
/usr/lib/libpurple.so.0(purple_ssl_close+0x62)[0xb6b2f4e2]
/usr/lib/libpurple.so.0(+0x8b58b)[0xb6b2f58b]
/usr/lib/libpurple.so.0(+0x75015)[0xb6b19015]
/usr/lib/libpurple.so.0(+0x75182)[0xb6b19182]
pidgin(+0x6b90b)[0xb774090b]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x8a8c5)[0xb6c628c5]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x13e)[0xb6c1e83e]
/lib/i386-linux-gnu/libglib-2.0.so.0(+0x46be8)[0xb6c1ebe8]
/lib/i386-linux-gnu/libglib-2.0.so.0(g_main_loop_run+0x7b)[0xb6c1f04b]
/usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0(gtk_main+0xb0)[0xb70ba3e0]
pidgin(main+0xa24)[0xb76fda34]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf5)[0xb68aa905]
pidgin(+0x29205)[0xb76fe205]
======= Memory map: ========
adc4f000-adccf000 rw-s 00000000 00:04 2654219    /SYSV00000000 (deleted)
adccf000-add2e000 r--p 00000000 08:01 3540752    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-RI.ttf
addae000-addcf000 r--p 00000000 08:01 4069655    /usr/share/fonts/truetype/openoffice/opens___.ttf
addcf000-ade84000 r--p 00000000 08:01 3540701    /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
ade84000-aded6000 r--p 00000000 08:01 3540703    /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
aded6000-adf1f000 r-xp 00000000 08:01 2886693    /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
adf1f000-adf20000 r--p 00048000 08:01 2886693    /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
adf20000-adf21000 rw-p 00049000 08:01 2886693    /usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
adf21000-adf31000 rw-p 00000000 00:00 0 
adf45000-adfa5000 rw-s 00000000 00:04 2293769    /SYSV00000000 (deleted)
adfa5000-ae005000 rw-s 00000000 00:04 2261000    /SYSV00000000 (deleted)
ae005000-ae0ae000 r--p 00000000 08:01 3540700    /usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf
ae0ae000-ae100000 r--p 00000000 08:01 3540744    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf
ae100000-ae13e000 rw-p 00000000 00:00 0 
ae13e000-ae1e8000 r-xp 00000000 08:01 2884891    /usr/lib/libaspell.so.15.2.0
ae1e8000-ae1eb000 r--p 000aa000 08:01 2884891    /usr/lib/libaspell.so.15.2.0
ae1eb000-ae1ec000 rw-p 000ad000 08:01 2884891    /usr/lib/libaspell.so.15.2.0
ae1ec000-ae1f0000 rw-p 00000000 00:00 0 
ae1f0000-ae241000 r-xp 00000000 08:01 2886690    /usr/lib/i386-linux-gnu/libhunspell-1.3.so.0.0.0
ae241000-ae242000 r--p 00050000 08:01 2886690    /usr/lib/i386-linux-gnu/libhunspell-1.3.so.0.0.0
ae242000-ae246000 rw-p 00051000 08:01 2886690    /usr/lib/i386-linux-gnu/libhunspell-1.3.so.0.0.0
ae246000-ae29d000 r--p 00000000 08:01 3540751    /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
ae29d000-b3400000 r--p 00000000 08:01 3410112    /usr/share/icons/gnome/icon-theme.cache
b3400000-b3421000 rw-p 00000000 00:00 0 
b3421000-b3500000 ---p 00000000 00:00 0 
b3508000-b350c000 r-xp 00000000 08:01 2887542    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b350c000-b350d000 r--p 00003000 08:01 2887542    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b350d000-b350e000 rw-p 00004000 08:01 2887542    /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
b350e000-b3510000 r-xp 00000000 08:01 2887469    /usr/lib/i386-linux-gnu/gconv/ISO8859-1.so
b3510000-b3511000 r--p 00001000 08:01 2887469    /usr/lib/i386-linux-gnu/gconv/ISO8859-1.so
b3511000-b3512000 rw-p 00002000 08:01 2887469    /usr/lib/i386-linux-gnu/gconv/ISO8859-1.so
b3512000-b3519000 r--s 00000000 08:01 2887525    /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b3519000-b3524000 r-xp 00000000 08:01 2887260    /usr/lib/i386-linux-gnu/enchant/libenchant_ispell.so
b3524000-b3525000 r--p 0000a000 08:01 2887260    /usr/lib/i386-linux-gnu/enchant/libenchant_ispell.so
b3525000-b3526000 rw-p 0000b000 08:01 2887260    /usr/lib/i386-linux-gnu/enchant/libenchant_ispell.so
b3526000-b352f000 r-xp 00000000 08:01 2887259    /usr/lib/i386-linux-gnu/enchant/libenchant_hspell.so
b352f000-b3530000 r--p 00008000 08:01 2887259    /usr/lib/i386-linux-gnu/enchant/libenchant_hspell.so
b3530000-b3532000 rw-p 00009000 08:01 2887259    /usr/lib/i386-linux-gnu/enchant/libenchant_hspell.so
b3532000-b3534000 r-xp 00000000 08:01 2887258    /usr/lib/i386-linux-gnu/enchant/libenchant_aspell.so
b3534000-b3535000 r--p 00001000 08:01 2887258    /usr/lib/i386-linux-gnu/enchant/libenchant_aspell.so
b3535000-b3536000 rw-p 00002000 08:01 2887258    /usr/lib/i386-linux-gnu/enchant/libenchant_aspell.so
b3536000-b353a000 r-xp 00000000 08:01 2887261    /usr/lib/i386-linux-gnu/enchant/libenchant_myspell.so
b353a000-b353b000 r--p 00003000 08:01 2887261    /usr/lib/i386-linux-gnu/enchant/libenchant_myspell.so
b353b000-b353c000 rw-p 00004000 08:01 2887261    /usr/lib/i386-linux-gnu/enchant/libenchant_myspell.so
b353c000-b3544000 r--s 00000000 08:01 1835067    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-4
b3544000-b3548000 r--s 00000000 08:01 1835057    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-4
b3548000-b354b000 r--s 00000000 08:01 1835063    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-4
b354b000-b357a000 r--s 00000000 08:01 1842053    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-4
b357a000-b358b000 r-xp 00000000 08:01 3670034    /lib/i386-linux-gnu/libudev.so.1.3.5
b358b000-b358c000 r--p 00010000 08:01 3670034    /lib/i386-linux-gnu/libudev.so.1.3.5
b358c000-b358d000 rw-p 00011000 08:01 3670034    /lib/i386-linux-gnu/libudev.so.1.3.5
b358d000-b35bf000 r-xp 00000000 08:01 2887749    /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
b35bf000-b35c1000 r--p 00032000 08:01 2887749    /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
b35c1000-b35c2000 rw-p 00034000 08:01 2887749    /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
b35c2000-b35fb000 r-xp 00000000 08:01 2886379    /usr/lib/i386-linux-gnu/libcroco-0.6.so.3.0.1
b35fb000-b35fd000 r--p 00038000 08:01 2886379    /usr/lib/i386-linux-gnu/libcroco-0.6.so.3.0.1
b35fd000-b35fe000 rw-p 0003a000 08:01 2886379    /usr/lib/i386-linux-gnu/libcroco-0.6.so.3.0.1
b35fe000-b35ff000 ---p 00000000 00:00 0 
b35ff000-b3dff000 rw-p 00000000 00:00 0 Aborted (core dumped)

---

### Post by rubiselprieto on 2014-05-26
I have the same problem

---

### Post by rubiselprieto on 2014-06-06
I am solived this problem remove de .gtkrc-2.0 in my home.

---

