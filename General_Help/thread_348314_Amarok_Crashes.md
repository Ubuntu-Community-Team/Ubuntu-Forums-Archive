---
title: "Amarok Crashes"
date: 2007-01-28
forum: General Help
---

### Post by Happy_Man on 2007-01-28
Amarok, for me, simply won't work. Whenever I try to open it, it immediately opens KMail, and gives me a bug error. This is what it looks like:

> ======== DEBUG INFORMATION  =======
Version:    1.4.4
Engine:     xine-engine
Build date: Jan 15 2007
CC version: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
KDElibs:    3.5.5
Qt:         3.3.7
TagLib:     1.4.0
CPU count:  1
NDEBUG:     true
==== file /usr/lib/amarok/amarokapp =======
/usr/lib/amarok/amarokapp: symbolic link to `/usr/bin/amarokapp'


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1261462752 (LWP 16977)]
[New Thread -1274791024 (LWP 16980)]
0xb7f7a410 in ?? ()
#0  0xb7f7a410 in ?? ()
#1  0xbf9dc528 in ?? ()
#2  0xb737bc78 in ?? () from /usr/lib/libkdecore.so.4
#3  0x00000004 in ?? ()
#4  0xb684cfc6 in access () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7279061 in KIconThemeDir::iconPath () from /usr/lib/libkdecore.so.4
#6  0xb7279217 in KIconTheme::iconPath () from /usr/lib/libkdecore.so.4
#7  0xb72794e5 in KIconLoader::findMatchingIcon ()
   from /usr/lib/libkdecore.so.4
#8  0xb72990ce in KIconLoader::loadIcon () from /usr/lib/libkdecore.so.4
#9  0xb7caf6f6 in MediaBrowser::MediaBrowser () from /usr/lib/libamarok.so.0
#10 0xb7d92742 in PlaylistWindow::init () from /usr/lib/libamarok.so.0
#11 0xb7b6a4ce in App::continueInit () from /usr/lib/libamarok.so.0
#12 0xb7b6ae38 in App::qt_invoke () from /usr/lib/libamarok.so.0
#13 0xb62b2787 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#14 0xb663e884 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#15 0xb62d271a in QSignal::activate () from /usr/lib/libqt-mt.so.3
#16 0xb62da130 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#17 0xb62499a8 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#18 0xb624b7d7 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#19 0xb72f8bc2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#20 0xb61dc1a9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#21 0xb623c3f3 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#22 0xb61f0ce5 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#23 0xb626407e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#24 0xb6263e8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#25 0xb624b551 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#26 0x0804bf09 in ?? ()
#27 0xbf9dd69c in ?? ()
#28 0xbf9dd834 in ?? ()
#29 0x00000013 in ?? ()
#30 0x08067d15 in ?? ()
#31 0x00000000 in ?? ()
#0  0xb7f7a410 in ?? ()
No symbol table info available.
#1  0xbf9dc528 in ?? ()
No symbol table info available.
#2  0xb737bc78 in ?? () from /usr/lib/libkdecore.so.4
No symbol table info available.
#3  0x00000004 in ?? ()
No symbol table info available.
#4  0xb684cfc6 in access () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb7279061 in KIconThemeDir::iconPath () from /usr/lib/libkdecore.so.4
No symbol table info available.
#6  0xb7279217 in KIconTheme::iconPath () from /usr/lib/libkdecore.so.4
No symbol table info available.
#7  0xb72794e5 in KIconLoader::findMatchingIcon ()
   from /usr/lib/libkdecore.so.4
No symbol table info available.
#8  0xb72990ce in KIconLoader::loadIcon () from /usr/lib/libkdecore.so.4
No symbol table info available.
#9  0xb7caf6f6 in MediaBrowser::MediaBrowser () from /usr/lib/libamarok.so.0
No symbol table info available.
#10 0xb7d92742 in PlaylistWindow::init () from /usr/lib/libamarok.so.0
No symbol table info available.
#11 0xb7b6a4ce in App::continueInit () from /usr/lib/libamarok.so.0
No symbol table info available.
#12 0xb7b6ae38 in App::qt_invoke () from /usr/lib/libamarok.so.0
No symbol table info available.
#13 0xb62b2787 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#14 0xb663e884 in QSignal::signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#15 0xb62d271a in QSignal::activate () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#16 0xb62da130 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#17 0xb62499a8 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#18 0xb624b7d7 in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#19 0xb72f8bc2 in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#20 0xb61dc1a9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#21 0xb623c3f3 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#22 0xb61f0ce5 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#23 0xb626407e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#24 0xb6263e8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#25 0xb624b551 in QApplication::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#26 0x0804bf09 in ?? ()
No symbol table info available.
#27 0xbf9dd69c in ?? ()
No symbol table info available.
#28 0xbf9dd834 in ?? ()
No symbol table info available.
#29 0x00000013 in ?? ()
No symbol table info available.
#30 0x08067d15 in ?? ()
No symbol table info available.
#31 0x00000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 2 (Thread -1274791024 (LWP 16980)):
#0  0xb7f7a410 in ?? ()
#1  0xb4041e28 in ?? ()
#2  0x00000000 in ?? ()
Thread 1 (Thread -1261462752 (LWP 16977)):
#0  0xb7f7a410 in ?? ()
#1  0xbf9dc528 in ?? ()
#2  0xb737bc78 in ?? () from /usr/lib/libkdecore.so.4
#3  0x00000004 in ?? ()
#4  0xb684cfc6 in access () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7279061 in KIconThemeDir::iconPath () from /usr/lib/libkdecore.so.4
#6  0xb7279217 in KIconTheme::iconPath () from /usr/lib/libkdecore.so.4
#7  0xb72794e5 in KIconLoader::findMatchingIcon ()
   from /usr/lib/libkdecore.so.4
#8  0xb72990ce in KIconLoader::loadIcon () from /usr/lib/libkdecore.so.4
#9  0xb7caf6f6 in MediaBrowser::MediaBrowser () from /usr/lib/libamarok.so.0
#10 0xb7d92742 in PlaylistWindow::init () from /usr/lib/libamarok.so.0
#11 0xb7b6a4ce in App::continueInit () from /usr/lib/libamarok.so.0
#12 0xb7b6ae38 in App::qt_invoke () from /usr/lib/libamarok.so.0
#13 0xb62b2787 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#14 0xb663e884 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#15 0xb62d271a in QSignal::activate () from /usr/lib/libqt-mt.so.3
#16 0xb62da130 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#17 0xb62499a8 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#18 0xb624b7d7 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#19 0xb72f8bc2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#20 0xb61dc1a9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#21 0xb623c3f3 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#22 0xb61f0ce5 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#23 0xb626407e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#24 0xb6263e8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#25 0xb624b551 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#26 0x0804bf09 in ?? ()
#27 0xbf9dd69c in ?? ()
#28 0xbf9dd834 in ?? ()
#29 0x00000013 in ?? ()
#30 0x08067d15 in ?? ()
#31 0x00000000 in ?? ()
#0  0xb7f7a410 in ?? ()


==== kdBacktrace() ================


When I try to force uninstall, Konsole tells me that my "kubuntu-desktop" package is broken. Eh? :confused: If someone could please help me out, that would be most appreciated!

---

### Post by Skeorx13 on 2007-03-21
I also have this issue whenever I try to delete a track from an imported playlist. It tries to open up kmail for some crazy reason and crashes amarok. Does anyone know a fix for this?

---

### Post by fabuntu on 2007-03-29
I fixed that with :

mv $HOME/.kde/share/apps/amarok/collection.db $HOME/.kde/share/apps/amarok/collection.db.old

Then rebuild the collection.

I don't have a better solution.

Fabrice

---

