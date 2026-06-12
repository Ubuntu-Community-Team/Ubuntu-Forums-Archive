---
title: "Ktorrent crash"
date: 2007-07-22
forum: General Help
---

### Post by glynallinson on 2007-07-22
Ktorrent runs for few hours then seems to crash, not sure what to do

back trace:
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
[Thread debugging using libthread_db enabled]
[New Thread -1235634480 (LWP 11616)]
[New Thread -1296340080 (LWP 11622)]
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb7df6bcb in dht::ParseRsp () from /usr/lib/libktorrent-2.1.so
#7  0xb7df6df2 in dht::MakeRPCMsg () from /usr/lib/libktorrent-2.1.so
#8  0xb7debf51 in dht::RPCServer::readPacket ()
   from /usr/lib/libktorrent-2.1.so
#9  0xb7dec252 in dht::RPCServer::qt_invoke ()
   from /usr/lib/libktorrent-2.1.so
#10 0xb6e3088b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb6e31330 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb75ba04c in KNetwork::KClientSocketBase::readyRead ()
   from /usr/lib/libkdecore.so.4
#13 0xb75ba086 in KNetwork::KClientSocketBase::slotReadActivity ()
   from /usr/lib/libkdecore.so.4
#14 0xb75cc143 in KNetwork::KClientSocketBase::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#15 0xb75cc1e6 in KNetwork::KDatagramSocket::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#16 0xb6e3088b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb6e311a2 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb71bd877 in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#19 0xb6e5344a in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#20 0xb6dc7a60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb6dc988f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb758bce2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb6d5a1e9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#24 0xb6db9e59 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#25 0xb6d6ed07 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#26 0xb6de2136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#27 0xb6de1f46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#28 0xb6dc9609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#29 0x080653d6 in ?? ()
#30 0xb65e1ebc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x08064ec1 in ?? ()

---

### Post by userundefine on 2007-07-22
I've experienced consistent crashes with ktorrent as well.  Unbearably so.

You might want to try upgrading to the [latest version](http://packages.ubuntu.com/feisty-backports/net/ktorrent), however, as 2.1 is quite old.  Feisty version there.

---

