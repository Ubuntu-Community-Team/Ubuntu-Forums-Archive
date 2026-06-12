---
title: "Kubuntu 16.04: Plasma crashes at boot, says can't find OpenGL2"
date: 2017-02-17
forum: General Help
---

### Post by gobstopper2 on 2017-02-17
Hello Everyone, I'm running Kubuntu 16.04 on a workstation with a Nvidia Quadro K5200 graphics card. I had things up an running(other than not being able to enable indirect GLX), and then tried to change the default sddm theme, which then caused login problems. I thought I had reverted everything back and was able to connect normally via NoMachine(remote Desktop) but now when I try to connect I get a black screen with two messages. The first says "Plasma is unable to start as it could not correctly use OpenGL 2. Please check that your graphic drivers are set up correctly." and the second one had on occasion shown a Krunner error, but this time around it just mentioned plasma.

For some background info: I installed Nvidia-375 and ran sudo nvidia-xconfig
I've run sudo apt-get update 
and      sudo apt-get upgrade

Below is the error message in the "Developer Information" Tab"
```

Application: Plasma (plasmashell), signal: Aborted
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[Current thread is 1 (Thread 0x7fd1c7b7d8c0 (LWP 2891))]

Thread 3 (Thread 0x7fd1b11a7700 (LWP 2896)):
#0  0x00007fd1c228669d in read () at ../sysdeps/unix/syscall-template.S:84
#1  0x00007fd1bf0636f0 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007fd1bf01fe74 in g_main_context_check () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007fd1bf020330 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007fd1bf02049c in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007fd1c2bb77eb in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#6  0x00007fd1c2b5eb4a in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#7  0x00007fd1c297b834 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#8  0x00007fd1c52233c5 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#9  0x00007fd1c29807be in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#10 0x00007fd1c1a6d6ba in start_thread (arg=0x7fd1b11a7700) at pthread_create.c:333
#11 0x00007fd1c229682d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 2 (Thread 0x7fd1b3dd4700 (LWP 2894)):
#0  0x00007fd1c228ab5d in poll () at ../sysdeps/unix/syscall-template.S:84
#1  0x00007fd1c634fc62 in ?? () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#2  0x00007fd1c63518d7 in xcb_wait_for_event () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#3  0x00007fd1b6554629 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
#4  0x00007fd1c29807be in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007fd1c1a6d6ba in start_thread (arg=0x7fd1b3dd4700) at pthread_create.c:333
#6  0x00007fd1c229682d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 1 (Thread 0x7fd1c7b7d8c0 (LWP 2891)):
[KCrash Handler]
#6  0x00007fd1c21c5428 in __GI_raise (sig=sig@entry=6) at ../sysdeps/unix/sysv/linux/raise.c:54
#7  0x00007fd1c21c702a in __GI_abort () at abort.c:89
#8  0x00007fd1c296df81 in QMessageLogger::fatal(char const*, ...) const () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#9  0x00007fd1c7d45bca in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/xcbglintegrations/libqxcb-glx-integration.so
#10 0x00007fd1c7d437cb in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/xcbglintegrations/libqxcb-glx-integration.so
#11 0x00007fd1b655ad11 in QXcbIntegration::createPlatformOpenGLContext(QOpenGLContext*) const () from /usr/lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
#12 0x00007fd1c2edc59d in QOpenGLContext::create() () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#13 0x00007fd1c7d4641a in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/xcbglintegrations/libqxcb-glx-integration.so
#14 0x00007fd1c7d465c1 in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/xcbglintegrations/libqxcb-glx-integration.so
#15 0x00007fd1c5c16c0b in QSGRenderLoop::instance() () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#16 0x00007fd1c5c49215 in QQuickWindowPrivate::init(QQuickWindow*, QQuickRenderControl*) () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#17 0x00007fd1c76f52ac in PlasmaQuick::Dialog::Dialog(QQuickItem*) () from /usr/lib/x86_64-linux-gnu/libKF5PlasmaQuick.so.5
#18 0x00007fd1abdc1fa0 in ?? () from /usr/lib/x86_64-linux-gnu/qt5/qml/org/kde/plasma/core/libcorebindingsplugin.so
#19 0x00007fd1c51bb71b in QQmlType::create() const () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#20 0x00007fd1c521ce24 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#21 0x00007fd1c521d8cf in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#22 0x00007fd1c51a8037 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#23 0x00007fd1c51a8924 in QQmlIncubationController::incubateFor(int) () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#24 0x00007fd1c5e8e7ac in ?? () from /usr/lib/x86_64-linux-gnu/libKF5Declarative.so.5
#25 0x00007fd1c51a8739 in QQmlEnginePrivate::incubate(QQmlIncubator&, QQmlContextData*) () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#26 0x00007fd1c51a3eac in QQmlComponent::create(QQmlIncubator&, QQmlContext*, QQmlContext*) () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#27 0x00007fd1c5e8b395 in KDeclarative::QmlObject::completeInitialization(QHash<QString, QVariant> const&) () from /usr/lib/x86_64-linux-gnu/libKF5Declarative.so.5
#28 0x00007fd1c5e8b44c in ?? () from /usr/lib/x86_64-linux-gnu/libKF5Declarative.so.5
#29 0x00007fd1c5e8b619 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5Declarative.so.5
#30 0x00000000004658cb in Osd::Osd(ShellCorona*) ()
#31 0x0000000000458425 in ShellCorona::ShellCorona(QObject*) ()
#32 0x0000000000461c7c in ShellManager::loadHandlers() ()
#33 0x00007fd1c2b90c01 in QObject::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#34 0x00007fd1c366405c in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5
#35 0x00007fd1c3669516 in QApplication::notify(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5
#36 0x00007fd1c2b6138b in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#37 0x00007fd1c2b63786 in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#38 0x00007fd1c2bb73c3 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#39 0x00007fd1bf020197 in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#40 0x00007fd1bf0203f0 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#41 0x00007fd1bf02049c in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#42 0x00007fd1c2bb77cf in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#43 0x00007fd1c2b5eb4a in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#44 0x00007fd1c2b66bec in QCoreApplication::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#45 0x0000000000432d4a in main ()
```

Any help would be greatly appreciated.

---

### Post by gobstopper2 on 2017-02-17
I tried to log in again via NoMachine, and this time the krunner error appeared as well.
in the details section of the window it says:

Executable: krunner PID: 2090 Signal: Aborted (6) Time: 2/17/17 14:35:28

In the error window it contains:

```

Application: krunner (krunner), signal: Aborted
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[Current thread is 1 (Thread 0x7fb21daaa8c0 (LWP 2090))]

Thread 2 (Thread 0x7fb20ab3b700 (LWP 2101)):
#0  0x00007fb21a4fab5d in poll () at ../sysdeps/unix/syscall-template.S:84
#1  0x00007fb2199ebc62 in ?? () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#2  0x00007fb2199ed8d7 in xcb_wait_for_event () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#3  0x00007fb20d2bb629 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
#4  0x00007fb21abf07be in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007fb21874a6ba in start_thread (arg=0x7fb20ab3b700) at pthread_create.c:333
#6  0x00007fb21a50682d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 1 (Thread 0x7fb21daaa8c0 (LWP 2090)):
[KCrash Handler]
#6  0x00007fb21a435428 in __GI_raise (sig=sig@entry=6) at ../sysdeps/unix/sysv/linux/raise.c:54
#7  0x00007fb21a43702a in __GI_abort () at abort.c:89
#8  0x00007fb21abddf81 in QMessageLogger::fatal(char const*, ...) const () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#9  0x00007fb21dc50bca in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/xcbglintegrations/libqxcb-glx-integration.so
#10 0x00007fb21dc4e7cb in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/xcbglintegrations/libqxcb-glx-integration.so
#11 0x00007fb20d2c1d11 in QXcbIntegration::createPlatformOpenGLContext(QOpenGLContext*) const () from /usr/lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
#12 0x00007fb21b14c59d in QOpenGLContext::create() () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#13 0x00007fb21dc5141a in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/xcbglintegrations/libqxcb-glx-integration.so
#14 0x00007fb21dc515c1 in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/xcbglintegrations/libqxcb-glx-integration.so
#15 0x00007fb21cf41c0b in QSGRenderLoop::instance() () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#16 0x00007fb21cf74215 in QQuickWindowPrivate::init(QQuickWindow*, QQuickRenderControl*) () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#17 0x00007fb21d8082ac in PlasmaQuick::Dialog::Dialog(QQuickItem*) () from /usr/lib/x86_64-linux-gnu/libKF5PlasmaQuick.so.5
#18 0x0000000000408a1e in View::View(QWindow*) ()
#19 0x00000000004075e9 in main ()



```

I was unable to post an image, but basically it's a black screen with 3 pop up windows containing the messages.

---

