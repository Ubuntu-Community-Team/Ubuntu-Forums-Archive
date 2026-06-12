---
title: "Ktorrent Keeps crashing since Feisty upgrade"
date: 2007-04-23
forum: General Help
---

### Post by Steve H on 2007-04-23
Hey people,

I´ve always enjoyed using Ktorrent since moving over to Ubuntu, but now since the Feisty upgrade it keeps crashing. IT keeps starting the KDE Crash Handler which gives the following in the backtrace:

> (no debugging symbols found)
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
[New Thread -1235391856 (LWP 9583)]
[New Thread -1248449648 (LWP 9585)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0xb7df650b in dht::ParseRsp () from /usr/lib/libktorrent-2.1.so
#7  0xb7df6732 in dht::MakeRPCMsg () from /usr/lib/libktorrent-2.1.so
#8  0xb7deb5d1 in dht::RPCServer::readPacket ()
   from /usr/lib/libktorrent-2.1.so
#9  0xb7deb8d2 in dht::RPCServer::qt_invoke ()
   from /usr/lib/libktorrent-2.1.so
#10 0xb6e6b88b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb6e6c330 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb75e650c in KNetwork::KClientSocketBase::readyRead ()
   from /usr/lib/libkdecore.so.4
#13 0xb75e6546 in KNetwork::KClientSocketBase::slotReadActivity ()
   from /usr/lib/libkdecore.so.4
#14 0xb75f9723 in KNetwork::KClientSocketBase::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#15 0xb75f97c6 in KNetwork::KDatagramSocket::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#16 0xb6e6b88b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb6e6c1a2 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb71f8877 in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#19 0xb6e8e44a in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#20 0xb6e02a60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb6e0488f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb75b2d62 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb6d951e9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#24 0xb6df4e59 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#25 0xb6da9d07 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#26 0xb6e1d136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#27 0xb6e1cf46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#28 0xb6e04609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#29 0x08063de6 in ?? ()
#30 0xb661cebc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x080638d1 in ?? ()



Any ideas what is causing it? It looks like a dependency thing to me, but I don´t know how to fix it.

Help!! If you can´t help please suggest a decent torrent client (not the hog known as Azureus though!). Is deluge any good?!

---

### Post by zvacet on 2007-04-23
Did you try to reinstall it with Adept?

---

### Post by Steve H on 2007-04-23
Adept? I know what that is.

I have reinstalled it several times now, as well as reinstalling all my KDE apps and kdelibs. Just to let you know i using Gnome, not KDE.

---

### Post by montag on 2007-04-23
Same problem here!
Now I tried renaming my ktorrentrc config file, so ktorrent created a new one (keeping all the torrents I was downloading).
Now let's see how does it works...

---

### Post by Steve H on 2007-04-23
I´ve given up on Ktorrent for the time being, until they get it sorted.

I´m trying [_Deluge_]("http://deluge-torrent.org/index.php"), It´s still in development, but I reckon it will be worth sticking with , and helping to develop.

Give it some support and let´s turn it in to something worth bragging about........

8-)

---

### Post by montag on 2007-04-24
Renaming /home/user_name/.kde/share/config/ktorrentrc, and so letting ktorrent create a new one at the next startup, did the trick!
It's running for 22 hours, now: great!

---

### Post by hazelkid on 2007-04-25
Removing ktorrentrc didn't work for me. Ktorrent keeps crashing :(

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
[New Thread -1235286320 (LWP 16489)]
[New Thread -1250387056 (LWP 16506)]
[New Thread -1241994352 (LWP 16505)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0xb7e4b46b in dht::ParseRsp () from /usr/lib/libktorrent-2.1.3.so
#7  0xb7e4b692 in dht::MakeRPCMsg () from /usr/lib/libktorrent-2.1.3.so
#8  0xb7e406c2 in dht::RPCServer::readPacket ()
   from /usr/lib/libktorrent-2.1.3.so
#9  0xb7e409e2 in dht::RPCServer::qt_invoke ()
   from /usr/lib/libktorrent-2.1.3.so
#10 0xb6e8588b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb6e86330 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb760f04c in KNetwork::KClientSocketBase::readyRead ()
   from /usr/lib/libkdecore.so.4
#13 0xb760f086 in KNetwork::KClientSocketBase::slotReadActivity ()
   from /usr/lib/libkdecore.so.4
#14 0xb7621143 in KNetwork::KClientSocketBase::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#15 0xb76211e6 in KNetwork::KDatagramSocket::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#16 0xb6e8588b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb6e861a2 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb7212877 in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#19 0xb6ea844a in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#20 0xb6e1ca60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb6e1e88f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb75e0ce2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb6daf1e9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#24 0xb6e0ee59 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#25 0xb6dc3d07 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#26 0xb6e37136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#27 0xb6e36f46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#28 0xb6e1e609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#29 0x08065487 in ?? ()
#30 0xb6636ebc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x08064f01 in ?? ()

```

---

### Post by lqyjzmms on 2007-04-25
I was affected by this annoying bug as well. After turning of distributed hash tables (DHT), the official version included in feisty (based on KTorrent 2.1.0 at the moment) seems to be stable again.

On the official KTorrent web site, there is a deb file of [KTorrent v2.1.4]("http://ktorrent.org/forum/viewtopic.php?t=1539") for Ubuntu Feisty Fawn. The KTorrent admin said: > People experiencing the DHT crash, should also upgrade. I will try that one now.

---

### Post by montag on 2007-04-25
> **lqyjzmms said:**
> I was affected by this annoying bug as well. After turning of distributed hash tables (DHT), the official version included in feisty (based on KTorrent 2.1.0 at the moment) seems to be stable again.

Maybe the problem was really DHT: I used to have that turned on (and Ktorrent was crashing), but with the new config file I forgot to reactivate...

> **lqyjzmms said:**
> 
On the official KTorrent web site, there is a deb file of [KTorrent v2.1.4]("http://ktorrent.org/forum/viewtopic.php?t=1539") for Ubuntu Feisty Fawn. The KTorrent admin said:  I will try that one now.

Downloading now! ;-)

---

### Post by pickarooney on 2007-04-26
I've been having this problem for the last week also, but haven't upgraded to Feisty Fawn (yet). 
I'm on version 2.1 and have just turned off DHT to test.
Will I be able to upgrade to 2.1.4 from Edgy?

---

### Post by lqyjzmms on 2007-04-26
Just follow the link from my previous post. KTorrent.org offers deb files of KTorrent v2.1.4 for feisty, edgy and even dapper.

---

### Post by ChrisNiemy on 2007-04-26
Hey everyone,

**thanks a lot**! Had this issue also, but now working almost perfectly.

Installing the .deb of 2.1.4 Version (as described in the posts before) and then removing/renaming the /home/<your username/.kde/share/config/ktorrentrc file worked it out! :)

I just had to adjust some settings again, which were reset to default values (like ports etc.)

Thanks again!

PS: Running now without a crash since over 10 hours. With the version before it crashed quite early.

---

### Post by lqyjzmms on 2007-04-26
I reckon you do not even have to delete your preferences file (ktorrentrc).
It looks like distributed hash tables (DHTs) cause problems in v2.1.

So your options are either to deactivate DHTs and stick with v2.1, or to upgrade to v2.1.4 if you want to continue using DHTs. Please notice that you probably will not get any automatic security updates for ktorrent from the feisty repositories if you upgrade to v2.1.4.

---

### Post by fj4 on 2007-04-26
> **montag said:**
> Renaming /home/user_name/.kde/share/config/ktorrentrc, and so letting ktorrent create a new one at the next startup, did the trick!
It's running for 22 hours, now: great!

This also worked for me, on 2.1.

---

### Post by montag on 2007-04-26
> **fj4 said:**
> This also worked for me, on 2.1.

Yes, but now you have probably DHT deactivated.

I thing the best solution is to install the deb of Ktorrent 2.1.4 (some posts back). Now I've DHT perfectly working.

My 2 cents

---

### Post by pickarooney on 2007-04-28
I installed 2.14, reactivated DHT and KTorrent still keeps crashing.

---

### Post by hazelkid on 2007-04-28
The problem is not only with feisty. 2.1.3 used to crash a lot in my Edgy. Installing 2.1 from kubuntu repositories solved this issues. Yesterday I updated to 2.1.4 and still running without any crash yet. (3GB down)

---

### Post by Steve H on 2007-05-01
After dabbling with Deluge, and not really getting on with it, it reinstalled Ktorrent again the other day on a fresh Feisty install. The error has returned, but having looked through this thread it looks like you folk have sorted this.

I will download this latest version from the site and have a look to see if the dreaded DHT error returns. I hope not, it's getting really annoying now, and I don't want to turn off the DHT!!

Thanks again people for helping get to the bottom of this.

:)

---

### Post by Melhisedek on 2007-05-01
Getting the same error, will try installing 2.1.4 and keep you folks updated...

---

### Post by Steve H on 2007-05-03
I've dumped the repo version of Ktorrent 2.x and downloaded/installed the newer 2.1.4 from the [_website_]("http://ktorrent.org").

No problems as of yet, 20 hours and counting.

Looks like the new version works a charm!!

Cheers for the help people!!

:)

---

### Post by Drakene on 2007-05-08
I'm quite new to ubuntu & all things linux, so I'm sorry if I'm asking something silly.... Updated to feisty a couple of days ago. Ktorrent working ok until last night. Now it displays "Cannot talk to klauncher" on launching. Tried reinstalling it, but the problem persists.

---

### Post by Steve H on 2007-05-08
Drakene, I had a similar problem, there are several ways to sort it. 

First you could just launch ¨kdeinit¨, either using alt-f2 or from a terminal. Then open ktorrent again and see how that goes. 

Alternatively you could add kdeinit to your session startup (system --> session --> new startup program), but you´ll have to try the first method to make sure that kdeinit can actually launch. You don´t want set a startup program that doesn´t work.

If you can be bothered with that uninstall ktorrent with all its recommended dependencies. If you right click on Ktorrent in Synaptic, you will see ¨Mark Recommended for Installation¨ look for kdebase, kdelibs, kdesktop etc and uninstall the lot, Then reinstall everything. This method is only recommended if you are running Gnome, you don want to do it if you are actually running KDE, cos it will kill your desktop.

Hope that helps, let me know how it goes.

:)

---

### Post by Drakene on 2007-05-08
Thanks Steve! I am running Gnome. Tried your second option. Everything&#347; working ok now!

---

### Post by kelvin spratt on 2007-05-08
folks i told everybody this in another thread to download 2.1.4 weeks ago all thats happening is people are duplicating the same threads over and over again please check previous threads before starting new one

---

### Post by Steve H on 2007-05-08
I thought the 2.1.4 problem is related to the DHT error, not the KDE launcher problem , that some other folks are experiencing?!

---

