---
title: "Amarok Crashing when deleting songs from Ipod"
date: 2008-04-04
forum: General Help
---

### Post by tj111 on 2008-04-04
When attempting to delete songs from my Ipod nano, Amarok gets to ~20% then crashes every time.  It threw an error message saying it couldn't find Kmail, so I installed that, and it still crashes, but puts the following error information into Kmail.

> 


======== DEBUG INFORMATION  =======
Version:    1.4.8
Engine:     xine-engine
Build date: Mar 11 2008
CC version: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
KDElibs:    3.5.8
Qt:         3.3.7
TagLib:     1.4.0
CPU count:  2
NDEBUG:     true
==== file `which amarokapp` =======
/usr/bin/amarokapp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1262856480 (LWP 24265)]
[New Thread -1391465584 (LWP 24317)]
[New Thread -1342428272 (LWP 24315)]
[New Thread -1334035568 (LWP 24314)]
[New Thread -1323754608 (LWP 24313)]
[New Thread -1287251056 (LWP 24312)]
[New Thread -1315361904 (LWP 24271)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb67a66db in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0x0804d431 in Amarok::Crash::crashHandler ()
#3  <signal handler called>
#4  0xb69497bd in __dynamic_cast () from /usr/lib/libstdc++.so.6
#5  0xb3de2678 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
#6  0xb3de2970 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
#7  0xb3de2970 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
#8  0xb7cd63a1 in MediaDevice::deleteFromDevice ()
   from /usr/lib/libamarok.so.0
#9  0xb7cd6810 in MediaView::keyPressEvent () from /usr/lib/libamarok.so.0
#10 0xb62708a3 in QWidget::event () from /usr/lib/libqt-mt.so.3
#11 0xb74d36c2 in KListView::event () from /usr/lib/libkdeui.so.4
#12 0xb61d0af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#13 0xb61d2ac0 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#14 0xb7303cd2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#15 0xb616327d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#16 0xb6153c69 in QETWidget::translateKeyEvent () from /usr/lib/libqt-mt.so.3
#17 0xb616004f in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#18 0xb61771a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#19 0xb61eb1ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#20 0xb61eafde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#21 0xb61d2699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#22 0x0804bfa2 in ?? ()
#23 0xbfedf8e0 in ?? ()
#24 0xbfedfa74 in ?? ()
#25 0x0806a806 in ?? ()
#26 0x0806a7f5 in ?? ()
#27 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb67a66db in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0x0804d431 in Amarok::Crash::crashHandler ()
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb69497bd in __dynamic_cast () from /usr/lib/libstdc++.so.6
No symbol table info available.
#5  0xb3de2678 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
No symbol table info available.
#6  0xb3de2970 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
No symbol table info available.
#7  0xb3de2970 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
No symbol table info available.
#8  0xb7cd63a1 in MediaDevice::deleteFromDevice ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#9  0xb7cd6810 in MediaView::keyPressEvent () from /usr/lib/libamarok.so.0
No symbol table info available.
#10 0xb62708a3 in QWidget::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#11 0xb74d36c2 in KListView::event () from /usr/lib/libkdeui.so.4
No symbol table info available.
#12 0xb61d0af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#13 0xb61d2ac0 in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#14 0xb7303cd2 in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#15 0xb616327d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#16 0xb6153c69 in QETWidget::translateKeyEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#17 0xb616004f in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#18 0xb61771a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#19 0xb61eb1ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#20 0xb61eafde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#21 0xb61d2699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#22 0x0804bfa2 in ?? ()
No symbol table info available.
#23 0xbfedf8e0 in ?? ()
No symbol table info available.
#24 0xbfedfa74 in ?? ()
No symbol table info available.
#25 0x0806a806 in ?? ()
No symbol table info available.
#26 0x0806a7f5 in ?? ()
No symbol table info available.
#27 0x00000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 7 (Thread -1315361904 (LWP 24271)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb52948fc in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb67f4374 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb2bfb4cf in ?? () from /usr/lib/libxine.so.1
#4  0x085252c0 in ?? ()
#5  0x085252a8 in ?? ()
#6  0xb1992388 in ?? ()
#7  0x00000000 in ?? ()
Thread 6 (Thread -1287251056 (LWP 24312)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb67dd5e7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb1f4f29b in ?? ()
   from /usr/lib/xine/plugins/1.1.10/xineplug_ao_out_alsa.so
#3  0xb34612e8 in ?? ()
#4  0x00000001 in ?? ()
#5  0x0000014d in ?? ()
#6  0xb4ba7700 in ?? ()
#7  0x00000001 in ?? ()
#8  0xb3461330 in ?? ()
#9  0xb346136c in ?? ()
#10 0x08553b40 in ?? ()
#11 0xb34612e8 in ?? ()
#12 0xa0cbc62e in ?? ()
#13 0x00000000 in ?? ()
Thread 5 (Thread -1323754608 (LWP 24313)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb67dd5e7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb21bfd74 in snd_pcm_wait_nocheck () from /usr/lib/libasound.so.2
#3  0xb21bff5f in snd_pcm_wait () from /usr/lib/libasound.so.2
#4  0xb1f4f907 in ?? ()
   from /usr/lib/xine/plugins/1.1.10/xineplug_ao_out_alsa.so
#5  0x08bd41c8 in ?? ()
#6  0x000003e8 in ?? ()
#7  0x0000006c in ?? ()
#8  0x08ce6790 in ?? ()
#9  0x0000045b in ?? ()
#10 0xb1191290 in ?? ()
#11 0xb7fa9e73 in ?? () from /lib/ld-linux.so.2
#12 0xb2c0cf5e in ?? () from /usr/lib/libxine.so.1
#13 0x08553ac8 in ?? ()
#14 0x086519d8 in ?? ()
#15 0x0000045b in ?? ()
#16 0x00000000 in ?? ()
Thread 4 (Thread -1334035568 (LWP 24314)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb52948fc in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb67f4374 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb2c0a202 in ?? () from /usr/lib/libxine.so.1
#4  0x08ce7190 in ?? ()
#5  0x08ce7178 in ?? ()
#6  0xb07c328c in ?? ()
#7  0x00000400 in ?? ()
#8  0xb677ffc0 in malloc () from /lib/tls/i686/cmov/libc.so.6
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
Thread 3 (Thread -1342428272 (LWP 24315)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb5294676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb67f431d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb2c0fe00 in xine_event_wait () from /usr/lib/libxine.so.1
#4  0x086ce100 in ?? ()
#5  0x086fe878 in ?? ()
#6  0x00000001 in ?? ()
#7  0xb2c0fe8c in ?? () from /usr/lib/libxine.so.1
#8  0x086fe878 in ?? ()
#9  0x086ce100 in ?? ()
#10 0x086fe87c in ?? ()
#11 0xb529fff4 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#12 0x00000000 in ?? ()
Thread 2 (Thread -1391465584 (LWP 24317)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb5294676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb67f431d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb2bfedfc in ?? () from /usr/lib/libxine.so.1
#4  0x08cf1218 in ?? ()
#5  0x08cf1200 in ?? ()
#6  0x08cf1174 in ?? ()
#7  0xaf7915b4 in ?? () from /home/tj/.xine/plugins/1.1.10/xineplug_dmx_qt.so
#8  0x00000163 in ?? ()
#9  0x00000000 in ?? ()
Thread 1 (Thread -1262856480 (LWP 24265)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb67a66db in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0x0804d431 in Amarok::Crash::crashHandler ()
#3  <signal handler called>
#4  0xb69497bd in __dynamic_cast () from /usr/lib/libstdc++.so.6
#5  0xb3de2678 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
#6  0xb3de2970 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
#7  0xb3de2970 in IpodMediaDevice::deleteItemFromDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
#8  0xb7cd63a1 in MediaDevice::deleteFromDevice ()
   from /usr/lib/libamarok.so.0
#9  0xb7cd6810 in MediaView::keyPressEvent () from /usr/lib/libamarok.so.0
#10 0xb62708a3 in QWidget::event () from /usr/lib/libqt-mt.so.3
#11 0xb74d36c2 in KListView::event () from /usr/lib/libkdeui.so.4
#12 0xb61d0af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#13 0xb61d2ac0 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#14 0xb7303cd2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#15 0xb616327d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#16 0xb6153c69 in QETWidget::translateKeyEvent () from /usr/lib/libqt-mt.so.3
#17 0xb616004f in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#18 0xb61771a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#19 0xb61eb1ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#20 0xb61eafde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#21 0xb61d2699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#22 0x0804bfa2 in ?? ()
#23 0xbfedf8e0 in ?? ()
#24 0xbfedfa74 in ?? ()
#25 0x0806a806 in ?? ()
#26 0x0806a7f5 in ?? ()
#27 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


==== kdBacktrace() ================


Any help is appreciated.

---

