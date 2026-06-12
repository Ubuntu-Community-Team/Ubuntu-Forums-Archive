---
title: "[SOLVED] Adept / Synaptic not working (backtrace inc.)"
date: 2008-01-15
forum: General Help
---

### Post by FleetAdmiral74 on 2008-01-15
edit: i ran some dkpg -a command the terminal suggested, seems to have fixed the problem.

So I'm in kubuntu, on a fairly fresh install, But it always tells me there is another package management process running. Heres what I see

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found) x a billion
[Thread debugging using libthread_db enabled]
[New Thread -1235929408 (LWP 5882)]
(no debugging symbols found) x a billion again
[KCrash handler]
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb65ae875 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb65b0201 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb67ba6e0 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb67b7f65 in ?? () from /usr/lib/libstdc++.so.6
#11 0xb67b7fa2 in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb67b80ca in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0x08116f26 in ?? ()
#14 0x0811749a in ?? ()
#15 0x081174f8 in ?? ()
#16 0x08117d45 in ?? ()
#17 0x0811583d in ?? ()
#18 0x080ff989 in ?? ()
#19 0x08082bbd in ?? ()
#20 0x080711fa in ?? ()
#21 0x08071554 in ?? ()
#22 0xb6dfe893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb718a8ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#24 0xb6e1e842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#25 0xb6e26258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#26 0xb6d95af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#27 0xb6d9791f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0xb755bca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#29 0xb6d28209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#30 0xb6d8853b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#31 0xb6d3cd49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb6db01ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#33 0xb6daffde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#34 0xb6d97699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#35 0x0806e7b5 in ?? ()
#36 0xb659a050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#37 0x0806e501 in ?? ()

```

Its mostly greek to me, with some source code thrown in there

---

