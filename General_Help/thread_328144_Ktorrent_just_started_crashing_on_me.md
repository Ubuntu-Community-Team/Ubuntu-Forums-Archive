---
title: "Ktorrent just started crashing on me"
date: 2006-12-30
forum: General Help
---

### Post by bdmp on 2006-12-30
Ktorrent just started crashing on me. Can anyone tell me how I can fix it? This is the out put when I start it in the command line [http://paste.ubuntu-nl.org/39490/](http://paste.ubuntu-nl.org/39490/) and this is what the crash handler says [http://paste.ubuntu-nl.org/39491/](http://paste.ubuntu-nl.org/39491/) Thanks

---

### Post by Nigel Warner on 2007-01-01
same here, it has been working fine for ages...

---

### Post by bdmp on 2007-01-02
The command line output:
burepe@pikapika:~$ ktorrent
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
WARNING: please edit ~/.scim/global and change /DefaultConfigModule to kconfig
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
terminate called after throwing an instance of 'bt::Error'
DCOP aborting (delayed) call from 'anonymous-31863' to 'ktorrent'
KCrash: Application 'ktorrent' crashing...
ERROR: Communication problem with ktorrent, it probably crashed.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x36001b1
burepe@pikapika:~$ X Error: BadDevice, invalid or uninitialized input device 166  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


The crash handler:

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
[Thread debugging using libthread_db enabled]
[New Thread -1232275776 (LWP 31977)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb69219a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb69232b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb6affc1e in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb6afd915 in __gxx_personality_v0 () from /usr/lib/libstdc++.so.6
#11 0xb6afd94a in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb6afdad8 in __cxa_rethrow () from /usr/lib/libstdc++.so.6
#13 0xb7f82e6b in bt::MultiFileCache::downloadStatusChanged ()
   from /usr/lib/libktorrent.so.0
#14 0xb7f5a4ab in bt::ChunkManager::downloadStatusChanged ()
   from /usr/lib/libktorrent.so.0
#15 0xb7f5a708 in bt::ChunkManager::qt_invoke () from /usr/lib/libktorrent.so.0
#16 0xb70efeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb7f88b72 in bt::TorrentFile::downloadStatusChanged ()
   from /usr/lib/libktorrent.so.0
#18 0xb7f88c67 in bt::TorrentFile::setDoNotDownload ()
   from /usr/lib/libktorrent.so.0
#19 0xb7f5abf8 in bt::ChunkManager::loadFileInfo ()
   from /usr/lib/libktorrent.so.0
#20 0xb7f5ac7b in bt::ChunkManager::loadIndexFile ()
   from /usr/lib/libktorrent.so.0
#21 0xb7f6cf35 in bt::TorrentControl::init () from /usr/lib/libktorrent.so.0
#22 0x0806a532 in kt::CompareVal<unsigned long> ()
#23 0x0806a95f in kt::CompareVal<unsigned long> ()
#24 0x0805d758 in QGList::count ()
#25 0x0806e7e1 in QValueList<QString>::detachInternal ()
#26 0xb781c610 in KUniqueApplication::processDelayed ()
   from /usr/lib/libkdecore.so.4
#27 0xb781dd87 in KUniqueApplication::qt_invoke ()
   from /usr/lib/libkdecore.so.4
#28 0x0806e447 in QValueList<QString>::detachInternal ()
#29 0xb70efeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#30 0xb748329a in QSignal::signal () from /usr/lib/libqt-mt.so.3
#31 0xb710d630 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#32 0xb7115120 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#33 0xb7085e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#34 0xb7086052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#35 0xb780ad7d in KApplication::notify () from /usr/lib/libkdecore.so.4
#36 0xb7017157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#37 0xb7077843 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#38 0xb702af67 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#39 0xb709e947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#40 0xb709e86a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#41 0xb7084965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#42 0x0805b79f in ?? ()
#43 0xb690dea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#44 0x0805b451 in ?? ()


Sorry about that...

---

### Post by solderhead on 2007-01-04
ktorrent was working fine for me until I performed a system update.  the adept updater popped-up in my toolbar, so i did the update.  that's what killed ktorrent.  is there any way to roll back the updates?

---

### Post by solderhead on 2007-01-08
the folks at ktorrent said (as of December 19) this was a bug that was fixed "a long time ago."  they suggest updating to the newest beta version of ktorrent.

can anyone tell me how to do that in kubuntu?  i'm new to debian and i have no idea how to pull in a ktorrent beta.

thanks.

---

### Post by tito2502 on 2007-01-08
You could try grabbing the deb here

[Ktorrent  2.1 rc1 edgy deb]("http://buntudot.org/people/~jdong/ktorrent/2.1rc1/edgy/ktorrent_2.1~rc1-0ubuntu1~6.10prevu1_i386.deb")

That will upgrade you to the latest version

---

