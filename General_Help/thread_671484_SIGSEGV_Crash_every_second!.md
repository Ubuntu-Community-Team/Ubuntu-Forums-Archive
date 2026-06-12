---
title: "SIGSEGV Crash every second!"
date: 2008-01-18
forum: General Help
---

### Post by israelha on 2008-01-18
this happen when i try to use Konqueror and sometimes in Adept Manager and other Kde's programs, please i need some help here!!!

Thanks for helpers.

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
[New Thread -1236089152 (LWP 8134)]
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xbf6b0e1c in ?? ()
#7  0xb6bcd560 in QWidgetItem::setGeometry () from /usr/lib/libqt-mt.so.3
#8  0xb6c1f03d in QBoxLayout::setGeometry () from /usr/lib/libqt-mt.so.3
#9  0xb6bcc053 in QLayout::activate () from /usr/lib/libqt-mt.so.3
#10 0xb6bcc52e in QLayout::eventFilter () from /usr/lib/libqt-mt.so.3
#11 0xb6c39e40 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#12 0xb6c39ebe in QObject::event () from /usr/lib/libqt-mt.so.3
#13 0xb6c715b3 in QWidget::event () from /usr/lib/libqt-mt.so.3
#14 0xb6bd1af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#15 0xb6bd44ba in QApplication::notify () from /usr/lib/libqt-mt.so.3
#16 0xb72d9ca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#17 0xb6b64209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#18 0xb6bd2b28 in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#19 0xb6c73e5f in QWidget::show () from /usr/lib/libqt-mt.so.3
#20 0xb6c70cbf in QWidget::showChildren () from /usr/lib/libqt-mt.so.3
#21 0xb6c740f0 in QWidget::show () from /usr/lib/libqt-mt.so.3
#22 0xb6c70cbf in QWidget::showChildren () from /usr/lib/libqt-mt.so.3
#23 0xb6c740f0 in QWidget::show () from /usr/lib/libqt-mt.so.3
#24 0xb6dee605 in QDialog::show () from /usr/lib/libqt-mt.so.3
#25 0xb6def3cc in QDialog::exec () from /usr/lib/libqt-mt.so.3
#26 0xb75a9179 in KMessageBox::createKMessageBox ()
   from /usr/lib/libkdeui.so.4
#27 0xb75a98c7 in KMessageBox::createKMessageBox ()
   from /usr/lib/libkdeui.so.4
#28 0xb75ac14a in KMessageBox::warningYesNoCancelListWId ()
   from /usr/lib/libkdeui.so.4
#29 0xb75ac297 in KMessageBox::warningYesNoCancelList ()
   from /usr/lib/libkdeui.so.4
#30 0xb75ac30f in KMessageBox::warningYesNoCancel ()
   from /usr/lib/libkdeui.so.4
#31 0x0808910f in ?? ()
#32 0x0808999d in ?? ()
#33 0x08089adf in ?? ()
#34 0x080731da in ?? ()
#35 0x080755d5 in ?? ()
#36 0xb6c3a893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#37 0xb6fc68ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#38 0xb6c5a842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#39 0xb6c62258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#40 0xb6bd1af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#41 0xb6bd391f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#42 0xb72d9ca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#43 0xb6b64209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#44 0xb6bc453b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#45 0xb6b78d49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#46 0xb6bec1ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#47 0xb6bebfde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#48 0xb6bd3699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#49 0x08070345 in ?? ()
#50 0xb7666050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#51 0x08070091 in ?? ()
```

---

### Post by israelha on 2008-01-19
please some help:[

---

