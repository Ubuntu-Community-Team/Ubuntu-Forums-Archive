---
title: "I can print but not scan (segmentation fault)"
date: 2021-02-05
forum: General Help
---

### Post by buntu_hugenewbie11 on 2021-02-05
I can print to a network printer but I cannot scan.
When I use simplescan or xsane I get a segmentation fault.
I was previously able to scan until the latest round of updates with canon driver or escl.
The printer/scanner is on a wifi network and is MF644cdw cannon printer.

In running the command: scanimage -L -v

I get the error:
Segmentation fault (core dumped)

I am on kubuntu 20.04-64bit.

If anyone has ideas. Please help.

---

### Post by buntu_hugenewbie11 on 2021-02-06
When I run skanlite I get the following error trail to go with this. Is this a SANE issue?
> [COLOR="#808080"]Application: skanlite (skanlite), signal: Segmentation fault
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[Current thread is 1 (Thread 0x7f5832333c80 (LWP 57713))]

Thread 5 (Thread 0x7f582a089700 (LWP 57717)):
#0  0x00007f583596faff in __GI___poll (fds=0x7f582a088e00, nfds=2, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
#1  0x00007f58347891a2 in ?? () from /lib/x86_64-linux-gnu/libusb-1.0.so.0
#2  0x00007f5835047609 in start_thread (arg=<optimized out>) at pthread_create.c:477
#3  0x00007f583597c293 in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95

Thread 4 (Thread 0x7f582a90f700 (LWP 57716)):
[KCrash Handler]
#6  0x00007f582138a221 in ?? () from /usr/lib/x86_64-linux-gnu/sane/libsane-escl.so.1
#7  0x00007f582138a3c4 in ?? () from /usr/lib/x86_64-linux-gnu/sane/libsane-escl.so.1
#8  0x00007f5821388ffa in sanei_configure_attach () from /usr/lib/x86_64-linux-gnu/sane/libsane-escl.so.1
#9  0x00007f582138aa2d in sane_escl_get_devices () from /usr/lib/x86_64-linux-gnu/sane/libsane-escl.so.1
#10 0x00007f58358481ea in sane_dll_get_devices () from /usr/lib/x86_64-linux-gnu/libsane.so.1
#11 0x00007f5837674a9b in ?? () from /usr/lib/x86_64-linux-gnu/libKF5Sane.so.5
#12 0x00007f5835ceb9d2 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#13 0x00007f5835047609 in start_thread (arg=<optimized out>) at pthread_create.c:477
#14 0x00007f583597c293 in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95

Thread 3 (Thread 0x7f582bb20700 (LWP 57715)):
#0  0x00007f583596faff in __GI___poll (fds=0x7f58240029e0, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
#1  0x00007f58347e618e in ?? () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f58347e62c3 in g_main_context_iteration () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f5835f0b583 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#4  0x00007f5835eb24db in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007f5835cea785 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#6  0x00007f5836f73efa in ?? () from /usr/lib/x86_64-linux-gnu/libQt5DBus.so.5
#7  0x00007f5835ceb9d2 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#8  0x00007f5835047609 in start_thread (arg=<optimized out>) at pthread_create.c:477
#9  0x00007f583597c293 in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95

Thread 2 (Thread 0x7f583147f700 (LWP 57714)):
#0  0x00007f583596faff in __GI___poll (fds=0x7f583147eca8, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
#1  0x00007f583430ec1a in ?? () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#2  0x00007f583431090a in xcb_wait_for_event () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#3  0x00007f5831c77298 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
#4  0x00007f5835ceb9d2 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007f5835047609 in start_thread (arg=<optimized out>) at pthread_create.c:477
#6  0x00007f583597c293 in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95

Thread 1 (Thread 0x7f5832333c80 (LWP 57713)):
#0  0x00007f58347e55c6 in g_main_context_prepare () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#1  0x00007f58347e60bb in ?? () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f58347e62c3 in g_main_context_iteration () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f5835f0b583 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#4  0x00007f5835eb24db in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007f5836acfc6d in QDialog::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5
#6  0x00007f5837676961 in KSaneIface::KSaneWidget::selectDevice(QWidget*) () from /usr/lib/x86_64-linux-gnu/libKF5Sane.so.5
#7  0x0000560d36d8cb4e in ?? ()
#8  0x0000560d36d852d7 in ?? ()
#9  0x00007f58358810b3 in __libc_start_main (main=0x560d36d84a40, argc=5, argv=0x7ffecd13c708, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7ffecd13c6f8) at ../csu/libc-start.c:308
#10 0x0000560d36d854ce in _start ()
[Inferior 1 (process 57713) detached][/COLOR]

---

