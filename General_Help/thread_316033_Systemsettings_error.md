---
title: "Systemsettings error"
date: 2006-12-10
forum: General Help
---

### Post by freaz on 2006-12-10
Hi, I have problem with my Kubuntu Edgy Eft. Alway when I install nvidia drivers for my grafic card (geforce4 440 GP), start problems with systemsettings.

Problem is that it do only when I go to System Dettings => Desktop.
Just come there and after close window. I didnt make any changes, program call signal 11 (SIGSEGV). And really it is only in this subcategory..

Here is my Backtrace:

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
!!! this is there manytimes !!
[Thread debugging using libthread_db enabled]
[New Thread -1231903056 (LWP 4859)]
(no debugging symbols found)
!!! this is there manytimes !!!
[KCrash handler]
#6  0xb639d94f in glXChannelRectSyncSGIX () from /usr/lib/libGL.so.1
#7  0x08078408 in ?? ()
#8  0xb63d3660 in ?? () from /usr/lib/libGL.so.1
#9  0x08078408 in ?? ()
#10 0xb639c1a6 in glXChannelRectSyncSGIX () from /usr/lib/libGL.so.1
#11 0x08078408 in ?? ()
#12 0x08078408 in ?? ()
#13 0xb6a54208 in ?? () from /usr/lib/libX11.so.6
#14 0x08238db0 in ?? ()
#15 0xb699fddd in XCloseDisplay () from /usr/lib/libX11.so.6
#16 0xb6f02d14 in qt_cleanup () from /usr/lib/libqt-mt.so.3
#17 0xb6f7dc9e in QApplication::~QApplication () from /usr/lib/libqt-mt.so.3
#18 0xb7935849 in KApplication::~KApplication () from /usr/lib/libkdecore.so.4
#19 0x0805e8f9 in endl ()
#20 0xb7a488cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#21 0x08057fe1 in ?? ()

```

THX and I'm so sorry from my english..

---

