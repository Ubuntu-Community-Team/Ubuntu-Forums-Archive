---
title: "Ktorrent Start-up crash"
date: 2013-02-23
forum: General Help
---

### Post by Bill Gates Foundation on 2013-02-23
I have had this problem with Ktorrent.  I fixed it once before with deleting the contents of a file called shutdown_rules or something.......located in i think  the .kde/app/ktorrent folder....anyways i tried that and it still crashes on startup...

   >   p
 #18 0xb767a77e in bt::TorrentControl::continueStart (this=0x9b0fb18) at ../../src/torrent/torrentcontrol.cpp:461
 #19 0xb767b1a6 in bt::TorrentControl::start (this=0x9b0fb18) at ../../src/torrent/torrentcontrol.cpp:432
 #20 0xb758526a in kt::QueueManager::startSafely (this=0x97167f0, tc=0x9b0fb18) at ../../libktcore/torrent/queuemanager.cpp:731
 #21 0xb75853eb in startInternal (tc=0x9b0fb18, this=0x97167f0) at ../../libktcore/torrent/queuemanager.cpp:102
 #22 kt::QueueManager::startInternal (this=0x97167f0, tc=0x9b0fb18) at ../../libktcore/torrent/queuemanager.cpp:91
 #23 0xb7587334 in kt::Queuueue (this=0x97167f0) at ../../libktcore/torrent/queuemanager.cpp:588
 #24 0x08072c79 in kt::Core::qt_metacall (this=0x9882188, _c=QMetaObject::InvokeMetaMethod, _id=39, _a=0x9b2c828) at ./core.moc:194
 #25 0xb6770c9d in metacall (argv=0x9b2c828, idx=49, cl=QMetaObject::InvokeMetaMethod, object=0x9882188) at kernel/qmetaobject.cpp:245
 #26 QMetaObject::metacall (object=0x9882188, cl=QMetaObject::InvokeMetaMethod, idx=49, argv=0x9b2c828) at kernel/qmetaobject.cpp:240
 #27 0xb677bc35 in placeMetaCall (object=0x9882188, this=0x9b2c7c0) at kernel/qobject.cpp:527
 #28 QMetaCallEvent:laceMetaCall (this=0x9b2c7c0, object=0x9882188) at kernel/qobject.cpp:522
 #29 0xb6784c7b in QObject::event (this=0x9882188, e=0x9b2c7c0) at kernel/qobject.cpp:1195
 #30 0xb5c54ed4 in notify_helper (e=0x9b2c7c0, receiver=0x9882188, this=0x97297b8) at kernel/qapplication.cpp:4559
 #31 QApplicationPrivate::notify_helper (this=0x97297b8, receiver=0x9882188, e=0x9b2c7c0) at kernel/qapplication.cpp:4531
 #32 0xb5c5a30d in QApplication::notify (this=0x9b2c7c0, receiver=0x9882188, e=0x9b2c7c0) at kernel/qapplication.cpp:4288
 #33 0x08079937 in kt::App::notify (this=0xbfc10390, receiver=0x9882188, event=0x9b2c7c0) at ../../ktorrent/app.cpp:99
 #34 0xb676997e in QCoreApplication::notifyInternal (this=0xbfc10390, receiver=0x9882188, event=0x9b2c7c0) at kernel/qcoreapplication.cpp:876
 #35 0xb676dad8 in sendEvent (event=<optimized out>, receiver=<optimized out>) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:231
 #36 QCoreApplicationPrivate::sendPostedEvents (receiver=0x0, event_type=0, data=0x96e7370) at kernel/qcoreapplication.cpp:1500
 #37 0xb676de0c in QCoreApplication::sendPostedEvents (receiver=0x0, event_type=0) at kernel/qcoreapplication.cpp:1393
 #38 0xb679c494 in sendPostedEvents () at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:236
 #39 postEventSourceDispatch (s=0x971c808) at kernel/qeventdispatcher_glib.cpp:279
 #40 0xb4c9ad86 in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
 #41 0xb4c9b125 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 #42 0xb4c9b201 in g_main_context_iteration () from /lib/i386-linux-gnu/libglib-2.0.so.0
 #43 0xb679c887 in QEventDispatcherGliocessEvents (this=0x96e7ef0, flags=...) at kernel/qeventdispatcher_glib.cpp:424
 #44 0xb5d0daaa in QGuiEveis=0xbfc10304, flags=...) at kernel/qeventloop.cpp:149
 #46 0xb67687a9 in QEventLoop::exec (this=0xbfc10304, flags=...) at kernel/qeventloop.cpp:204
 #47 0xb676deba in QCoreApplication::exec () at kernel/qcoreapplication.cpp:1148
 #48 0xb5c52a74 in QApplication::exec () at kernel/qapplication.cpp:3820
 #49 0x080678a8 in main (argc=<error reading variable: Cannot access memory at address 0x74>, argv=<error reading variable: Cannot access memory at address 0x78>) at ../../ktorrent/main.cpp:177
 



---

### Post by Bill Gates Foundation on 2013-02-23
> Sat Feb 23 02:01:08 2013: Bound to 192.168.0.2:6881
Sat Feb 23 02:01:08 2013: UTP: bound to 192.168.0.2:6881
Sat Feb 23 02:01:08 2013: Cannot bind to port fe80::20d:81ff:fea2:25a8:6881 : Invalid argument
Sat Feb 23 02:01:08 2013: Bound to UDP port 6881
Sat Feb 23 02:01:08 2013: Bound to 192.168.0.2:6881
Sat Feb 23 02:01:08 2013: Cannot bind to port fe80::20d:81ff:fea2:25a8:6881 : Invalid argument
Sat Feb 23 02:01:08 2013: Bound to TCP port 6881
Sat Feb 23 02:01:08 2013: DHT: Starting on port 7881
Sat Feb 23 02:01:08 2013: DHT: Bound to 192.168.0.2:7881
Sat Feb 23 02:01:08 2013: Cannot bind to port fe80::20d:81ff:fea2:25a8:7881 : Invalid argument
Sat Feb 23 02:01:08 2013: DHT: Failed to bind to [fe80::20d:81ff:fea2:25a8]:7881
Sat Feb 23 02:01:08 2013: DHT: Loading bucket 134
Sat Feb 23 02:01:08 2013: DHT: Loading bucket 135
Sat Feb 23 02:01:08 2013: DHT: Loading bucket 136
Sat Feb 23 02:01:08 2013: DHT: Loading bucket 137
Sat Feb 23 02:01:08 2013: DHT: Loading bucket 138

> Sat Feb 23 02:01:10 2013: javascript
Sat Feb 23 02:01:10 2013: qtscript
Sat Feb 23 02:01:11 2013: Qt Debug: ktorrent(8464)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/ktsearchplugin.so" does not offer a qt_plugin_instance function.
Sat Feb 23 02:01:11 2013: Loading isohunt.com
Sat Feb 23 02:01:12 2013: Loading home page from /usr/share/kde4/apps/ktorrent/search/home/home.html
Sat Feb 23 02:01:12 2013: Qt Debug: ktorrent(8464)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/ktmagnetgeneratorplugin.so" does not offer a qt_plugin_instance function.
Sat Feb 23 02:01:12 2013: Qt Debug: ktorrent(8464)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/ktzeroconfplugin.so" does not offer a qt_plugin_instance function.
Sat Feb 23 02:01:12 2013: ZeroConf service added for MUSIC VIDEOS 
Sat Feb 23 02:01:12 2013: ZeroConf service added for Suits S02E16 HDTV x264-2HD[ettv]
Sat Feb 23 02:01:14 2013: Qt Debug: ktorrent(8464)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/ktshutdownplugin.so" does not offer a qt_plugin_instance function.
Sat Feb 23 02:01:14 2013: Failed to open file /home/desktop/.kde/share/apps/ktorrent/shutdown_rules : No such file or directory
Sat Feb 23 02:01:14 2013: Qt Debug: ktorrent(8464)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/ktdownloadorderplugin.so" does not offer a qt_plugin_instance function.
Sat Feb 23 02:01:14 2013: Qt Debug: ktorrent(8464)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/ktinfowidgetplugin.so" does not offer a qt_plugin_instance function.
Sat Feb 23 02:01:14 2013: Qt Debug: ktorrent(8464)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/ktmediaplayerplugin.so" does not offer a qt_plugin_instance function.
Sat Feb 23 02:01:16 2013: Qt Debug: ktorrent(8464)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/ktstatsplugin.so" does not offer a qt_plugin_instance function.
Sat Feb 23 02:01:16 2013: Started update timer
Sat Feb 23 02:01:16 2013: Failed to suppress sleeping
Sat Feb 23 02:01:16 2013: QM Starting: Suits S02E16 HDTV x264-2HD[ettv]
Sat Feb 23 02:01:16 2013: FreeBytes 1.13 GiB
Sat Feb 23 02:01:16 2013: Downloaded 0 B
Sat Feb 23 02:01:16 2013: Remaining 296.49 MiB
Sat Feb 23 02:01:16 2013: Starting download Suits S02E16 HDTV x264-2HD[ettv]

her is the log.......how do i delete the torrent list?

---

### Post by sanderj on 2013-02-23
Did you Google the last line ... ?

... seems like a known bug to me: [https://www.google.com/search?q=Cannot+access+memory+at+address+0x78>)+at+..%2F..%2Fktorrent%2Fmain.cpp%3A177]("https://www.google.com/search?q=Cannot+access+memory+at+address+0x78>)+at+..%2F..%2Fktorrent%2Fmain.cpp%3A177")

Workaround: use transmission.

HTH

---

### Post by matt_symes on 2013-02-23
Hi
> 
Workaround: use transmission.


I prefer rtorrent :D

Kind regards

---

### Post by sanderj on 2013-02-24
... and ... nothing ...?

OP, it would be nice if you followed up to the info you got.

---

