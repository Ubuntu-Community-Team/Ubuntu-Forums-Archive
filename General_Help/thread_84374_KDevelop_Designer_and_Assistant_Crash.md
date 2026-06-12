---
title: "KDevelop Designer and Assistant Crash"
date: 2005-10-30
forum: General Help
---

### Post by alvonsius on 2005-10-30
Hello there, is there anyone knows why everytime I started KDevelop Assistant and KDevelop Designer they always crash? Only those two that crash, the KDevelop itself doesn't have the same problem. Is there any component I missed or something? Or if I should reinstall all, how is the best way to do it?

Thanks for any answer

---

### Post by GoldBuggie on 2005-10-30
just for the record I have the same problem

---

### Post by meralon on 2005-10-31
Create a symlink from /usr/share/apps/kdevelop3 to /usr/share/apps/kdevelop.

```
ln -s /usr/share/apps/kdevelop3 /usr/share/apps/kdevelop
```

---

### Post by alvonsius on 2005-10-31
[QUOTE=meralon]Create a symlink from /usr/share/apps/kdevelop3 to /usr/share/apps/kdevelop.

```
ln -s /usr/share/apps/kdevelop3 /usr/share/apps/kdevelop
```[/QUOTE]

Wow, cool it works. Thanks meralon ...

---

### Post by xbaez on 2005-12-04
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1231989056 (LWP 12981)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#4  0xb6beeef1 in XCreateGC () from /usr/lib/libX11.so.6
#5  0xb705e8bb in qsincos () from /usr/lib/libqt-mt.so.3
#6  0xb705eee0 in qsincos () from /usr/lib/libqt-mt.so.3
#7  0xb705f301 in QPainter::updatePen () from /usr/lib/libqt-mt.so.3
#8  0xb7117d8f in QPainter::setPen () from /usr/lib/libqt-mt.so.3
#9  0xb724bd54 in QSplashScreen::drawContents () from /usr/lib/libqt-mt.so.3
#10 0xb724b910 in QSplashScreen::drawContents () from /usr/lib/libqt-mt.so.3
#11 0xb724b969 in QSplashScreen::repaint () from /usr/lib/libqt-mt.so.3
#12 0xb724baff in QSplashScreen::setPixmap () from /usr/lib/libqt-mt.so.3
#13 0xb724bba8 in QSplashScreen::QSplashScreen () from /usr/lib/libqt-mt.so.3
#14 0x0804eac4 in ?? ()
#15 0x081719f8 in ?? ()
#16 0xbfb0f33c in ?? ()
#17 0x00000000 in ?? ()
#18 0x00000000 in ?? ()
#19 0x00000000 in ?? ()
#20 0x00000001 in ?? ()
#21 0x0804fef8 in vtable for QGList ()
#22 0x00000000 in ?? ()
#23 0x00000000 in ?? ()
#24 0x0804fe64 in vtable for QGList ()
#25 0xb7f10838 in ?? () from /lib/ld-linux.so.2
#26 0x00000000 in ?? ()
#27 0xb7efa1ac in ?? ()
#28 0xbfb0f2b8 in ?? ()
#29 0xb7f027c9 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#30 0xb6957ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x0804e7c1 in ?? ()

That is the error I am receiving

HOW IN THE WORLD did you knew that?
It fixed, worked right away, the symlink was what I needed, thanks a lot!

---

