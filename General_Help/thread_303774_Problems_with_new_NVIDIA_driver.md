---
title: "Problems with new NVIDIA driver"
date: 2006-11-20
forum: General Help
---

### Post by ghepardo on 2006-11-20
I just installed the new nvidia driver from the script downloaded from their website.

Now when I start X the refresh is always setup at 45hz. I used nvidia settings (also in the kdesu mode) to modify it and save the xorg.conf file, but the problem persists.

Also when I close X there is a crash, I attach the crash info here:

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
[New Thread -1231903056 (LWP 12463)]
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
#6  0xb6783b25 in libhal_ctx_shutdown () from /usr/lib/libhal.so.1
#7  0xb67a3607 in KSMShutdownDlg::~KSMShutdownDlg ()
   from /usr/lib/libkdeinit_ksmserver.so
#8  0xb67a4ba5 in KSMShutdownDlg::confirmShutdown ()
   from /usr/lib/libkdeinit_ksmserver.so
#9  0xb67ada9d in KSMServer::shutdown () from /usr/lib/libkdeinit_ksmserver.so
#10 0xb67adcfd in KSMSaveYourselfRequestProc ()
   from /usr/lib/libkdeinit_ksmserver.so
#11 0xb6989ae3 in _SmsProcessMessage () from /usr/lib/libSM.so.6
#12 0xb697d40e in IceProcessMessages () from /usr/lib/libICE.so.6
#13 0xb67a861a in KSMServer::processData ()
   from /usr/lib/libkdeinit_ksmserver.so
#14 0xb67ae980 in KSMServer::qt_invoke () from /usr/lib/libkdeinit_ksmserver.so
#15 0xb72b9957 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#16 0xb72ba26e in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb7646cdb in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#18 0xb72dc516 in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#19 0xb7250b88 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#20 0xb72529b7 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#21 0xb7946db2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#22 0xb71e3389 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#23 0xb7242f81 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#24 0xb71f7ea7 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#25 0xb726b25e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#26 0xb726b06e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#27 0xb7252731 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#28 0xb67aa590 in kdemain () from /usr/lib/libkdeinit_ksmserver.so
#29 0xb67ca524 in kdeinitmain () from /usr/lib/kde3/ksmserver.so
#30 0x0804e4df in ?? ()
#31 0x00000001 in ?? ()
#32 0x080dedf0 in ?? ()
#33 0x00000001 in ?? ()
#34 0x00000000 in ?? ()



I hope someone can help me.

---

### Post by ghepardo on 2006-11-21
Up

---

