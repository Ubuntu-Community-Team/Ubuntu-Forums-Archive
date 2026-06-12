---
title: "ktorrent crashes in gnome ubuntu 7.04"
date: 2007-07-31
forum: General Help
---

### Post by rscott5 on 2007-07-31
Hi everyone,

I'm running ktorrent on my machine with Ubuntu 7.04 and Gnome. The problem I'm having is that it crashes at random times. It runs great when it is actually running, but then will just crash after a random interval of time. Sometimes it doesn't even crash at all, sometimes it will run for 4 hours and then crash, and other times it will crash after 10 minutes. I am going to post on the ktorrent.org forums too, but I figured I would check and see if anyone might be able to provide some insight here. The KDE Crash Handler comes up when ktorrent crashes and it says "Short description: The application KTorrent (ktorrent) crashed and caused the signal 11 (SIGSEGV)." I've posted the backtrace report below and attached a screenshot of the KDE Crash Handler. Thanks for your help.

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
[Thread debugging using libthread_db enabled]
[New Thread -1235548464 (LWP 13283)]
[New Thread -1240183920 (LWP 13299)]
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
#6  0xb7e0bbcb in dht::ParseRsp () from /usr/lib/libktorrent-2.1.so
#7  0xb7e0bdf2 in dht::MakeRPCMsg () from /usr/lib/libktorrent-2.1.so
#8  0xb7e00f51 in dht::RPCServer::readPacket ()
   from /usr/lib/libktorrent-2.1.so
#9  0xb7e01252 in dht::RPCServer::qt_invoke ()
   from /usr/lib/libktorrent-2.1.so
#10 0xb6e4588b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb6e46330 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb75cf04c in KNetwork::KClientSocketBase::readyRead ()
   from /usr/lib/libkdecore.so.4
#13 0xb75cf086 in KNetwork::KClientSocketBase::slotReadActivity ()
   from /usr/lib/libkdecore.so.4
#14 0xb75e1143 in KNetwork::KClientSocketBase::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#15 0xb75e11e6 in KNetwork::KDatagramSocket::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#16 0xb6e4588b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb6e461a2 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb71d2877 in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#19 0xb6e6844a in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#20 0xb6ddca60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb6dde88f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb75a0ce2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb6d6f1e9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#24 0xb6dcee59 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#25 0xb6d83d07 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#26 0xb6df7136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#27 0xb6df6f46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#28 0xb6dde609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#29 0x080653d6 in ?? ()
#30 0xb65f6ebc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x08064ec1 in ?? ()

```

---

### Post by FleetAdmiral74 on 2007-07-31
Same thing happened to me, pretty sure its a confirmed bug by now. 

In the mean time, might try Deluge. Have to use the .deb, but I really like it, compared to Azureus or BitTornado. 

And its been perfectly stable for me.

edit: I made multiple posts here and the ktorrent forums as well, never found a fix, just fyi.

---

### Post by AnRa on 2007-07-31
Try using [KTorrent 2.2](http://www.getdeb.net/app.php?name=KTorrent), it works perfectly well for me.

---

### Post by rscott5 on 2007-07-31
Ya I'm pretty sure that I am running 2.2, I think the repository has this newest version and that's where I got it from.

Thanks for the heads-up FleetAdmiral, I think I will put a post up on the ktorrent forum too and maybe we will start pressuring them to fix the bug ;-)

---

### Post by rscott5 on 2007-07-31
AnRa good tip, I guess I was wrong, the version in the Ubuntu repo is 2.1 and that is what I was running. 2.2 seems to be running okay, hasn't crashed yet but who knows. Thanks though.

FleetAdmiral - If you aren't running 2.2 then you should follow that link AnRa posted and download the newest version. They have a .deb package which makes the install really easy, good luck fixing.

---

### Post by AnRa on 2007-08-01
> **rscott5 said:**
> AnRa good tip, I guess I was wrong, the version in the Ubuntu repo is 2.1 and that is what I was running. 2.2 seems to be running okay, hasn't crashed yet but who knows. Thanks though.

FleetAdmiral - If you aren't running 2.2 then you should follow that link AnRa posted and download the newest version. They have a .deb package which makes the install really easy, good luck fixing.I realized you can also upgrade KTorrent to 2.2 by enabling the feisty-backports repository. Good luck! ;)

---

