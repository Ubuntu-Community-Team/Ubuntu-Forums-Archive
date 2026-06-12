---
title: "Issue with look and feel theme (repo?)"
date: 2019-05-14
forum: General Help
---

### Post by LMH1 on 2019-05-14
repo:
```
# deb cdrom:[Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416)]/ disco main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://no.archive.ubuntu.com/ubuntu/ disco main restricted

deb http://no.archive.ubuntu.com/ubuntu eoan main universe

# deb-src http://no.archive.ubuntu.com/ubuntu/ disco main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ disco-updates main restricted
# deb-src http://no.archive.ubuntu.com/ubuntu/ disco-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ disco universe
# deb-src http://no.archive.ubuntu.com/ubuntu/ disco universe
deb http://no.archive.ubuntu.com/ubuntu/ disco-updates universe
# deb-src http://no.archive.ubuntu.com/ubuntu/ disco-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://no.archive.ubuntu.com/ubuntu/ disco multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ disco multiverse
deb http://no.archive.ubuntu.com/ubuntu/ disco-updates multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ disco-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ disco-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ disco-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu disco partner
# deb-src http://archive.canonical.com/ubuntu disco partner

deb http://security.ubuntu.com/ubuntu disco-security main restricted
# deb-src http://security.ubuntu.com/ubuntu disco-security main restricted
deb http://security.ubuntu.com/ubuntu disco-security universe
# deb-src http://security.ubuntu.com/ubuntu disco-security universe
deb http://security.ubuntu.com/ubuntu disco-security multiverse
# deb-src http://security.ubuntu.com/ubuntu disco-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
```

I also get bug report:
```
  Application: Systeminnstillinger (systemsettings5), signal: Segmentation fault
 Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
 [Current thread is 1 (Thread 0x7f4eb79766c0 (LWP 8267))]
 

 Thread 13 (Thread 0x7f4e88ffb700 (LWP 9143)):
 #0  0x00007f4eba792916 in futex_reltimed_wait_cancelable (private=<optimized out>, reltime=0x7f4e88ffabd0, expected=0, futex_word=0x562abb1efbb4) at ../sysdeps/unix/sysv/linux/futex-internal.h:142
 #1  0x00007f4eba792916 in __pthread_cond_wait_common (abstime=0x7f4e88ffac80, mutex=0x562abb1efb60, cond=0x562abb1efb88) at pthread_cond_wait.c:533
 #2  0x00007f4eba792916 in __pthread_cond_timedwait (cond=0x562abb1efb88, mutex=0x562abb1efb60, abstime=0x7f4e88ffac80) at pthread_cond_wait.c:667
 #3  0x00007f4ebc3136b5 in QWaitCondition::wait(QMutex*, QDeadlineTimer) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #4  0x00007f4ebc3137e6 in QWaitCondition::wait(QMutex*, unsigned long) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007f4ebc310de1 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #6  0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #7  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #8  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 12 (Thread 0x7f4e897fc700 (LWP 9142)):
 #0  0x00007f4eba792916 in futex_reltimed_wait_cancelable (private=<optimized out>, reltime=0x7f4e897fbbd0, expected=0, futex_word=0x562abbf9a1d0) at ../sysdeps/unix/sysv/linux/futex-internal.h:142
 #1  0x00007f4eba792916 in __pthread_cond_wait_common (abstime=0x7f4e897fbc80, mutex=0x562abbf9a180, cond=0x562abbf9a1a8) at pthread_cond_wait.c:533
 #2  0x00007f4eba792916 in __pthread_cond_timedwait (cond=0x562abbf9a1a8, mutex=0x562abbf9a180, abstime=0x7f4e897fbc80) at pthread_cond_wait.c:667
 #3  0x00007f4ebc3136b5 in QWaitCondition::wait(QMutex*, QDeadlineTimer) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #4  0x00007f4ebc3137e6 in QWaitCondition::wait(QMutex*, unsigned long) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007f4ebc310de1 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #6  0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #7  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #8  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 11 (Thread 0x7f4e89ffd700 (LWP 9141)):
 #0  0x00007f4eba792916 in futex_reltimed_wait_cancelable (private=<optimized out>, reltime=0x7f4e89ffcbd0, expected=0, futex_word=0x562abb1ef8c4) at ../sysdeps/unix/sysv/linux/futex-internal.h:142
 #1  0x00007f4eba792916 in __pthread_cond_wait_common (abstime=0x7f4e89ffcc80, mutex=0x562abb1ef870, cond=0x562abb1ef898) at pthread_cond_wait.c:533
 #2  0x00007f4eba792916 in __pthread_cond_timedwait (cond=0x562abb1ef898, mutex=0x562abb1ef870, abstime=0x7f4e89ffcc80) at pthread_cond_wait.c:667
 #3  0x00007f4ebc3136b5 in QWaitCondition::wait(QMutex*, QDeadlineTimer) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #4  0x00007f4ebc3137e6 in QWaitCondition::wait(QMutex*, unsigned long) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007f4ebc310de1 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #6  0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #7  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #8  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 10 (Thread 0x7f4e8a7fe700 (LWP 9140)):
 #0  0x00007f4eba792916 in futex_reltimed_wait_cancelable (private=<optimized out>, reltime=0x7f4e8a7fdbd0, expected=0, futex_word=0x562abbffa610) at ../sysdeps/unix/sysv/linux/futex-internal.h:142
 #1  0x00007f4eba792916 in __pthread_cond_wait_common (abstime=0x7f4e8a7fdc80, mutex=0x562abbffa5c0, cond=0x562abbffa5e8) at pthread_cond_wait.c:533
 #2  0x00007f4eba792916 in __pthread_cond_timedwait (cond=0x562abbffa5e8, mutex=0x562abbffa5c0, abstime=0x7f4e8a7fdc80) at pthread_cond_wait.c:667
 #3  0x00007f4ebc3136b5 in QWaitCondition::wait(QMutex*, QDeadlineTimer) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #4  0x00007f4ebc3137e6 in QWaitCondition::wait(QMutex*, unsigned long) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007f4ebc310de1 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #6  0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #7  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #8  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 9 (Thread 0x7f4e8afff700 (LWP 8314)):
 #0  0x00007f4ebbf93729 in __GI___poll (fds=0x562ab9b5be70, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
 #1  0x00007f4eb9ce7cb6 in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007f4eb9ce8042 in g_main_loop_run () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007f4e98142c76 in  () at /lib/x86_64-linux-gnu/libgio-2.0.so.0
 #4  0x00007f4eb9d1098d in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #5  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #6  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 8 (Thread 0x7f4e9956e700 (LWP 8313)):
 #0  0x00007f4eb9d32960 in g_mutex_unlock () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #1  0x00007f4eb9ce7de6 in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007f4eb9ce7e21 in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007f4eb9d1098d in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #4  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #5  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 7 (Thread 0x7f4e9a875700 (LWP 8277)):
 #0  0x00007f4eb9ce4b67 in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #1  0x00007f4eb9ce7123 in g_main_context_prepare () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007f4eb9ce7beb in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007f4eb9ce7ddc in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #4  0x00007f4ebc516063 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007f4ebc4c15bb in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #6  0x00007f4ebc30c2c6 in QThread::exec() () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #7  0x00007f4ebb62def5 in  () at /lib/x86_64-linux-gnu/libQt5Qml.so.5
 #8  0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #9  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #10 0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 6 (Thread 0x7f4e9bfff700 (LWP 8275)):
 #0  0x00007f4eb9ce7c9c in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #1  0x00007f4eb9ce7ddc in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007f4ebc516063 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #3  0x00007f4ebc4c15bb in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #4  0x00007f4ebc30c2c6 in QThread::exec() () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007f4ebb62def5 in  () at /lib/x86_64-linux-gnu/libQt5Qml.so.5
 #6  0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #7  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #8  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 5 (Thread 0x7f4ea2a2b700 (LWP 8272)):
 #0  0x00007f4ebbf8efb4 in __GI___libc_read (nbytes=16, buf=0x7f4ea2a2ab20, fd=13) at ../sysdeps/unix/sysv/linux/read.c:26
 #1  0x00007f4ebbf8efb4 in __GI___libc_read (fd=13, buf=0x7f4ea2a2ab20, nbytes=16) at ../sysdeps/unix/sysv/linux/read.c:24
 #2  0x00007f4eb9d2e550 in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007f4eb9ce778f in g_main_context_check () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #4  0x00007f4eb9ce7c60 in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #5  0x00007f4eb9ce7ddc in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #6  0x00007f4ebc516063 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #7  0x00007f4ebc4c15bb in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #8  0x00007f4ebc30c2c6 in QThread::exec() () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #9  0x00007f4ebb62def5 in  () at /lib/x86_64-linux-gnu/libQt5Qml.so.5
 #10 0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #11 0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #12 0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 4 (Thread 0x7f4eadd6a700 (LWP 8270)):
 #0  0x00007f4eba7923bb in futex_wait_cancelable (private=<optimized out>, expected=0, futex_word=0x562ab376fdfc) at ../sysdeps/unix/sysv/linux/futex-internal.h:88
 #1  0x00007f4eba7923bb in __pthread_cond_wait_common (abstime=0x0, mutex=0x562ab376fda8, cond=0x562ab376fdd0) at pthread_cond_wait.c:502
 #2  0x00007f4eba7923bb in __pthread_cond_wait (cond=0x562ab376fdd0, mutex=0x562ab376fda8) at pthread_cond_wait.c:655
 #3  0x00007f4eae37036b in  () at /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
 #4  0x00007f4eae3700d7 in  () at /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
 #5  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #6  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 3 (Thread 0x7f4eb4880700 (LWP 8269)):
 #0  0x00007f4ebbf93729 in __GI___poll (fds=0x7f4ea80124a0, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
 #1  0x00007f4eb9ce7cb6 in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007f4eb9ce7ddc in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007f4ebc516063 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #4  0x00007f4ebc4c15bb in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007f4ebc30c2c6 in QThread::exec() () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #6  0x00007f4ebc78e565 in  () at /lib/x86_64-linux-gnu/libQt5DBus.so.5
 #7  0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #8  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #9  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 2 (Thread 0x7f4eb5dbc700 (LWP 8268)):
 #0  0x00007f4ebbf93729 in __GI___poll (fds=0x7f4eb5dbbc68, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
 #1  0x00007f4eba749917 in  () at /lib/x86_64-linux-gnu/libxcb.so.1
 #2  0x00007f4eba74b53a in xcb_wait_for_event () at /lib/x86_64-linux-gnu/libxcb.so.1
 #3  0x00007f4eb677d6a8 in  () at /lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
 #4  0x00007f4ebc30d612 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007f4eba78c182 in start_thread (arg=<optimized out>) at pthread_create.c:486
 #6  0x00007f4ebbf9fb1f in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 1 (Thread 0x7f4eb79766c0 (LWP 8267)):
 [KCrash Handler]
 #6  0x00007f4ebcca47c1 in QStandardItemModel::clear() () at /lib/x86_64-linux-gnu/libQt5Gui.so.5
 #7  0x00007f4e881b13fa in  () at /usr/lib/x86_64-linux-gnu/qt5/plugins/kcm_kamera.so
 #8  0x00007f4e881b2f38 in  () at /usr/lib/x86_64-linux-gnu/qt5/plugins/kcm_kamera.so
 #9  0x00007f4ebd87f4a9 in  () at /lib/x86_64-linux-gnu/libKF5ConfigWidgets.so.5
 #10 0x00007f4ebc4ecca2 in QObject::event(QEvent*) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #11 0x00007f4ebcf61feb in QWidget::event(QEvent*) () at /lib/x86_64-linux-gnu/libQt5Widgets.so.5
 #12 0x00007f4ebcf22551 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () at /lib/x86_64-linux-gnu/libQt5Widgets.so.5
 #13 0x00007f4ebcf29930 in QApplication::notify(QObject*, QEvent*) () at /lib/x86_64-linux-gnu/libQt5Widgets.so.5
 #14 0x00007f4ebc4c28e9 in QCoreApplication::notifyInternal2(QObject*, QEvent*) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #15 0x00007f4ebc4c5927 in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #16 0x00007f4ebc516a43 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #17 0x00007f4eb9ce7aae in g_main_context_dispatch () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #18 0x00007f4eb9ce7d48 in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #19 0x00007f4eb9ce7ddc in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #20 0x00007f4ebc516047 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #21 0x00007f4ebc4c15bb in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #22 0x00007f4ebc4c95e2 in QCoreApplication::exec() () at /lib/x86_64-linux-gnu/libQt5Core.so.5
 #23 0x0000562ab1ddc639 in  ()
 #24 0x00007f4ebbea8b6b in __libc_start_main (main=0x562ab1ddc250, argc=1, argv=0x7fff58d874c8, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7fff58d874b8) at ../csu/libc-start.c:308
 #25 0x0000562ab1ddc6ba in _start ()
 [Inferior 1 (process 8267) detached]


```

Hi can someone tell my why look and feel theme did not works?
Distribution is up to date, but some packes can not be installed:

dleyna-server dmeventd libdleyna-core-1.0-3 libgupnp-igd-1.0-4 libkf5prison5 xfwm4
6 is not available for upgrade.


[ATTACH=CONFIG]283258[/ATTACH]

---

### Post by slickymaster on 2019-05-14
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by LMH1 on 2019-05-14
Its not completly fixed, but i get away a lot of error, but i did not have option to go from this menu and charge setting there.
[https://pop.system76.com/docs/install-pop-theme/](https://pop.system76.com/docs/install-pop-theme/)
> 
sudo add-apt-repository ppa:system76/pop
sudo apt update
sudo apt install pop-theme

  It&#8217;s recommended to use the pop-theme metapackage, as this will pull in all components of the look. However, individual components can be installed separately, e.g.:

  sudo apt install pop-gtk-theme



Some idea why this give issue? Can this be reason?
[URL="https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa"]https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa
[/URL]

---

### Post by deadflowr on 2019-05-14
Why do you have the eoan repo enabled?
That's probably going to be an issue.

---

### Post by LMH1 on 2019-05-15
I have dissable as # the eoan repo.
Updated with APT-get upgrade
And reboot, but still the samme issue, its better with other computer.
So how to fix it without reinstall?

---

