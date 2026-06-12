---
title: "Kopete not working since upgrade to Gutsy Gibbon"
date: 2007-10-19
forum: General Help
---

### Post by MrNatewood on 2007-10-19
I have tried re-installing kopete with no success.
It crashes every time a minute or so after I start it, about two seconds after it starts connecting to the protocols, producing this bug report:
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
[New Thread -1241703952 (LWP 20814)]
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
(no debugging symbols found)
[KCrash handler]
#6  0xb59c711a in MSNAccount::slotNotifySocketClosed ()
   from /usr/lib/libkopete_msn_shared.so.0
#7  0xb59cf668 in MSNAccount::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#8  0xb6871893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#9  0xb6872338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0xb59d88dc in MSNSocket::socketClosed ()
   from /usr/lib/libkopete_msn_shared.so.0
#11 0xb59ec4cd in MSNNotifySocket::disconnect ()
   from /usr/lib/libkopete_msn_shared.so.0
#12 0xb59e8f3b in MSNNotifySocket::sslLoginFailed ()
   from /usr/lib/libkopete_msn_shared.so.0
#13 0xb59ef0f5 in MSNNotifySocket::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#14 0xb6871893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#15 0xb6872338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#16 0xb5a0916c in MSNSecureLoginHandler::loginFailed ()
   from /usr/lib/libkopete_msn_shared.so.0
#17 0xb5a0940f in MSNSecureLoginHandler::slotTweenerReceived ()
   from /usr/lib/libkopete_msn_shared.so.0
#18 0xb5a0a5a6 in MSNSecureLoginHandler::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#19 0xb6871893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#20 0xb74ac021 in KIO::Job::result () from /usr/lib/libkio.so.4
#21 0xb75048cd in KIO::Job::emitResult () from /usr/lib/libkio.so.4
#22 0xb7504d2e in KIO::SimpleJob::slotFinished () from /usr/lib/libkio.so.4
#23 0xb750543d in KIO::TransferJob::slotFinished () from /usr/lib/libkio.so.4
#24 0xb7504301 in KIO::SimpleJob::qt_invoke () from /usr/lib/libkio.so.4
#25 0xb7504363 in KIO::TransferJob::qt_invoke () from /usr/lib/libkio.so.4
#26 0xb6871893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#27 0xb6bfd8ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#28 0xb6891842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#29 0xb6899258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#30 0xb6808af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#31 0xb680a91f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#32 0xb6fceca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#33 0xb679b209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#34 0xb67fb53b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#35 0xb67afd49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#36 0xb68231ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#37 0xb6822fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#38 0xb680a699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#39 0x0807f95c in ?? ()
#40 0xbfe3e484 in ?? ()
#41 0xbfe3e47c in ?? ()
#42 0xbfe3e474 in ?? ()
#43 0x00000000 in ?? ()

```

This is the terminal output when run from terminal until it crashes:
```
VIDIOC_STREAMOFF error 22, Invalid argument
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: PKCS7_content_free
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OPENSSL_add_all_algorithms
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/libcrypto.so.0.9.8: undefined symbol: OpenSSL_add_all_algorithms_conf
QGDict::hashKeyString: Invalid null key
QGDict::hashKeyString: Invalid null key
kopete: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol ''.
kopete: 
KCrash: Application 'kopete' crashing...

```

This never happened before I upgraded to Gutsy. Can anyone help in making kopete work in Gutsy?

NOTE: I am using Ubuntu and not Kubuntu.

---

### Post by Xebec on 2007-10-19
Same thing here :( Any clues?

---

### Post by MrNatewood on 2007-10-19
> **Xebec said:**
> Same thing here :( Any clues?

Solved.
It is bug in kdelibs.
If you install this version it works:
[http://kubuntu.org/~jriddell/kdelibs4c2a_3.5.8-0ubuntu3_i386.deb](http://kubuntu.org/~jriddell/kdelibs4c2a_3.5.8-0ubuntu3_i386.deb)

---

