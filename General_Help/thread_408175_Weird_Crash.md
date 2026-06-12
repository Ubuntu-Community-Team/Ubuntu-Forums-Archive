---
title: "Weird Crash"
date: 2007-04-13
forum: General Help
---

### Post by buntu_hugenewbie11 on 2007-04-13
Can someone figure out why my konqueror keeps crashing??
Here is the log but it is unreadable to a layman such as my self.
Anyone have any idea?
Btw I'm using Feisty.


[KCrash handler]
#5  0x00002af2cc975f58 in KHTMLPart::khtmlMouseMoveEvent ()
   from /usr/lib/libkhtml.so.4
#6  0x00002af2c50873af in QObject::event () from /usr/lib/libqt-mt.so.3
#7  0x00002af2c5023156 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#8  0x00002af2c5024ee5 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#9  0x00002af2c49727a8 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#10 0x00002af2cc96fbb1 in KHTMLView::viewportMouseMoveEvent ()
   from /usr/lib/libkhtml.so.4
#11 0x00002af2c51b641b in QScrollView::eventFilter ()
   from /usr/lib/libqt-mt.so.3
#12 0x00002af2cc94da46 in KHTMLView::eventFilter ()
   from /usr/lib/libkhtml.so.4
#13 0x00002af2c5087261 in QObject::activate_filters ()
   from /usr/lib/libqt-mt.so.3
#14 0x00002af2c50872da in QObject::event () from /usr/lib/libqt-mt.so.3
#15 0x00002af2c50bc281 in QWidget::event () from /usr/lib/libqt-mt.so.3
#16 0x00002af2c5023156 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#17 0x00002af2c50252b4 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#18 0x00002af2c49727a8 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#19 0x00002af2c4fb5d34 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#20 0x00002af2c4fb493e in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#21 0x00002af2c4fb2b0a in QApplication::x11ProcessEvent ()
   from /usr/lib/libqt-mt.so.3
#22 0x00002af2c4fc93ea in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#23 0x00002af2c503c68b in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#24 0x00002af2c5024bba in QApplication::enter_loop ()
   from /usr/lib/libqt-mt.so.3
#25 0x00002af2c4fc60ab in QDragManager::drag () from /usr/lib/libqt-mt.so.3
#26 0x00002af2c50363f2 in QDragObject::drag () from /usr/lib/libqt-mt.so.3
#27 0x00002af2c5033b21 in QDragObject::drag () from /usr/lib/libqt-mt.so.3
#28 0x00002af2cc975f49 in KHTMLPart::khtmlMouseMoveEvent ()
   from /usr/lib/libkhtml.so.4
#29 0x00002af2c50873af in QObject::event () from /usr/lib/libqt-mt.so.3
#30 0x00002af2c5023156 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#31 0x00002af2c5024ee5 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#32 0x00002af2c49727a8 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#33 0x00002af2cc96fbb1 in KHTMLView::viewportMouseMoveEvent ()
   from /usr/lib/libkhtml.so.4
#34 0x00002af2c51b641b in QScrollView::eventFilter ()
   from /usr/lib/libqt-mt.so.3
#35 0x00002af2cc94da46 in KHTMLView::eventFilter ()
   from /usr/lib/libkhtml.so.4
#36 0x00002af2c5087261 in QObject::activate_filters ()
   from /usr/lib/libqt-mt.so.3
#37 0x00002af2c50872da in QObject::event () from /usr/lib/libqt-mt.so.3
#38 0x00002af2c50bc281 in QWidget::event () from /usr/lib/libqt-mt.so.3
#39 0x00002af2c5023156 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#40 0x00002af2c50252b4 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#41 0x00002af2c49727a8 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#42 0x00002af2c4fb5d34 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#43 0x00002af2c4fb493e in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#44 0x00002af2c4fb2b0a in QApplication::x11ProcessEvent ()
   from /usr/lib/libqt-mt.so.3
#45 0x00002af2c4fc93ea in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#46 0x00002af2c503c68b in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#47 0x00002af2c503c493 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#48 0x00002af2c5024c1c in QApplication::exec () from /usr/lib/libqt-mt.so.3
#49 0x00002af2ca46dc5c in kdemain () from /usr/lib/libkdeinit_konqueror.so
#50 0x0000000000407851 in ?? ()
#51 0x000000000040818c in ?? ()
#52 0x0000000000408535 in ?? ()
#53 0x00000000004095fa in ?? ()
#54 0x00002af2c3e698e4 in __libc_start_main () from /lib/libc.so.6
#55 0x0000000000404df9 in ?? ()
#56 0x00007fffe786b408 in ?? ()
#57 0x0000000000000000 in ?? ()

---

