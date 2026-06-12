---
title: "Kopete on Gusty - crashing when connecting with Windows Live Messenger"
date: 2007-12-08
forum: General Help
---

### Post by Aseld on 2007-12-08
Kopete's SIGSEGVing when I try to connect to my Windows Live Messenger account. I just reinstalled Ubuntu (because I messed around a bit too much and killed X and couldn't seem to fix it). I didn't have the problem with my previous installation. Everything seems to be fully updated. I notice that there was a similar bug in the Gutsy release candidate, but I'm using the latest version.

Here's the backtrace:

```

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

[Thread debugging using libthread_db enabled]
[New Thread -1241945616 (LWP 6374)]

[KCrash handler]
#6  0xb59e111a in MSNAccount::slotNotifySocketClosed ()
   from /usr/lib/libkopete_msn_shared.so.0
#7  0xb59e9668 in MSNAccount::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#8  0xb6836893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#9  0xb6837338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0xb59f28dc in MSNSocket::socketClosed ()
   from /usr/lib/libkopete_msn_shared.so.0
#11 0xb5a064cd in MSNNotifySocket::disconnect ()
   from /usr/lib/libkopete_msn_shared.so.0
#12 0xb5a02f3b in MSNNotifySocket::sslLoginFailed ()
   from /usr/lib/libkopete_msn_shared.so.0
#13 0xb5a090f5 in MSNNotifySocket::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#14 0xb6836893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#15 0xb6837338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#16 0xb5a2316c in MSNSecureLoginHandler::loginFailed ()
   from /usr/lib/libkopete_msn_shared.so.0
#17 0xb5a2340f in MSNSecureLoginHandler::slotTweenerReceived ()
   from /usr/lib/libkopete_msn_shared.so.0
#18 0xb5a245a6 in MSNSecureLoginHandler::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#19 0xb6836893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#20 0xb7471021 in KIO::Job::result () from /usr/lib/libkio.so.4
#21 0xb74c98cd in KIO::Job::emitResult () from /usr/lib/libkio.so.4
#22 0xb74c9d2e in KIO::SimpleJob::slotFinished () from /usr/lib/libkio.so.4
#23 0xb74ca43d in KIO::TransferJob::slotFinished () from /usr/lib/libkio.so.4
#24 0xb74c9301 in KIO::SimpleJob::qt_invoke () from /usr/lib/libkio.so.4
#25 0xb74c9363 in KIO::TransferJob::qt_invoke () from /usr/lib/libkio.so.4
#26 0xb6836893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#27 0xb6bc28ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#28 0xb6856842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#29 0xb685e258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#30 0xb67cdaf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#31 0xb67cf91f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#32 0xb6f93ca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#33 0xb6760209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#34 0xb67c053b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#35 0xb6774d49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#36 0xb67e81ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#37 0xb67e7fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#38 0xb67cf699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#39 0x0807f95c in ?? ()
#40 0xbff82064 in ?? ()
#41 0xbff8205c in ?? ()
#42 0xbff82054 in ?? ()
#43 0x00000000 in ?? ()

```

Any suggestions? Thanks a lot.

---

### Post by linuxwizard on 2007-12-08
Kubuntu's instant messenger application Kopete crashes when connecting with an account using MSN. A fix should be available from gutsy-updates soon.

Look at bottom of this page Kopete crashes when connecting to MSN
[https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

---

