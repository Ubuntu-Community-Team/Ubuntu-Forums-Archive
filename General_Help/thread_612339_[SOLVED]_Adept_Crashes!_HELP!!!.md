---
title: "[SOLVED] Adept Crashes! HELP!!!"
date: 2007-11-13
forum: General Help
---

### Post by ninja_in_pajamas on 2007-11-13
I just did a update through Adept Installer in Kubuntu 7.10.  It went through the installation process then gave me some error about not being able to complete the update due to possible compatibility issues or from a download not finishing before it tried to apply the update.  Now every time I try to start adept, even with the adept notifier process killed, it tells me that there is another program already running.  Here is the backtrace log.

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
[Thread debugging using libthread_db enabled]
[New Thread -1235634496 (LWP 5970)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#7  0xb65f6875 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb65f8201 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb68026e0 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb67fff65 in ?? () from /usr/lib/libstdc++.so.6
#11 0xb67fffa2 in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb68000ca in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0x0812b916 in ?? ()
#14 0x0812be8a in ?? ()
#15 0x0812bee8 in ?? ()
#16 0x0812c735 in ?? ()
#17 0x0812a22d in ?? ()
#18 0x08114379 in ?? ()
#19 0x080951ed in ?? ()
#20 0x0807378d in ?? ()
#21 0x0807408e in ?? ()
#22 0xb6e46893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb71d28ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#24 0xb6e66842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#25 0xb6e6e258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#26 0xb6dddaf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#27 0xb6ddf91f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0xb75a3ca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#29 0xb6d70209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#30 0xb6dd053b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#31 0xb6d84d49 in QEventLoop:: processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb6df81ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#33 0xb6df7fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#34 0xb6ddf699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#35 0x0806f75e in ?? ()
#36 0xb65e2050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#37 0x0806f401 in ?? ()


If anyone can help I would greatly appreciate it.


UPDATE:  Okay, if I run terminal and so a sudo apt-get update, then run adept, it works fine but oddly appears to be trying to open two instances at once.  If I do not run terminal first, then it still apppears to start two at once and crashes after I put in my password.  But if I put it into a run command then it starts without a hitch ( still tries to start two though).

---

### Post by ninja_in_pajamas on 2007-11-20
hmmmm....guess it's a good thing this problem went away on its own.

---

