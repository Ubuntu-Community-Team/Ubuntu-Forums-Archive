---
title: "webbrowser-app crashes?"
date: 2017-11-24
forum: General Help
---

### Post by eezacque on 2017-11-24
Message is as follows:

```

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.
MESA-LOADER: failed to retrieve device information
unity::action::ActionManager::ActionManager(QObject*):
    Could not determine application identifier. HUD will not work properly.
    Provide your application identifier in $APP_ID environment variable.
UCUriHandler: Empty "APP_ID" environment variable, ignoring.
file:///usr/share/webbrowser-app/webbrowser/ContentPickerDialog.qml:22:1: module "Ubuntu.Content" is not installed
file:///usr/share/webbrowser-app/webbrowser/ContentDownloadDialog.qml:22:1: module "Ubuntu.Content" is not installed
file:///usr/share/webbrowser-app/ContentHandler.qml:20:1: module "Ubuntu.Content" is not installed
file:///usr/share/webbrowser-app/webbrowser/DownloadHandler.qml:20:1: module "Ubuntu.DownloadManager" is not installed

(webbrowser-app:30839): IBUS-WARNING **: Unable to connect to ibus: Could not connect: Permission denied
MESA-LOADER: failed to retrieve device information
shm_open() failed: Permission denied

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.

(webbrowser-app:30839): dconf-CRITICAL **: unable to create file '/run/user/1000/dconf/user': Permission denied.  dconf will not work properly.
[1124/191958.554148:ERROR:child_thread_impl.cc(762)] Request for unknown Channel-associated interface: ui::mojom::GpuMain
qml: Loaded 8 UA override(s) from file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Web/ua-overrides-mobile.js
OxideQQuickWebView: canGoForward is deprecated. Please use the API provided by OxideQQuickNavigationHistory instead
OxideQQuickWebView: canGoBack is deprecated. Please use the API provided by OxideQQuickNavigationHistory instead
TouchSelectionController::active is deprecated, use TouchSelectionController::status instead
QOpenGLShader: could not create shader
intel_do_flush_locked failed: Invalid argument
[1124/191958.592919:FATAL:oxide_browser_process_main.cc(472)] Check failed: state_ == STATE_NOT_STARTED || state_ == STATE_SHUTDOWN. BrowserProcessMain::Shutdown() should be called before process exit
#0 0x7fa97f5dc63e <unknown>
#1 0x7fa97f5f637e <unknown>
#2 0x7fa980c17579 <unknown>
#3 0x7fa9bfb96ff8 <unknown>
#4 0x7fa9bfb97045 exit
#5 0x7fa9a97e368e <unknown>
#6 0x7fa9a97e955c <unknown>
#7 0x7fa9a97e9729 <unknown>
#8 0x7fa9a97eef0b <unknown>
#9 0x7fa9a95d2e7c <unknown>
#10 0x7fa9a97f024a <unknown>
#11 0x7fa9a95c301b <unknown>
#12 0x7fa9a95c3286 <unknown>
#13 0x7fa9a95c3688 <unknown>
#14 0x7fa9c14cfd16 QOpenGLTextureGlyphCache::fillTexture()
#15 0x7fa9c145bfc1 QTextureGlyphCache::fillInPendingGlyphs()
#16 0x7fa9c1b8cdb7 <unknown>
#17 0x7fa9c1b8ac4c <unknown>
#18 0x7fa9c1c14677 <unknown>
#19 0x7fa9c1c18a9c <unknown>
#20 0x7fa9c1c15547 <unknown>
#21 0x7fa9c1c13cb8 QQuickText::updatePaintNode()
#22 0x7fa9c1bd22d8 QQuickWindowPrivate::updateDirtyNode()
#23 0x7fa9c1bd2b4b QQuickWindowPrivate::updateDirtyNodes()
#24 0x7fa9c1bd2cc0 QQuickWindowPrivate::syncSceneGraph()
#25 0x7fa9c1ba112c <unknown>
#26 0x7fa9c1ba2aa6 <unknown>
#27 0x7fa9c11c22b5 QWindow::event()
#28 0x7fa9c1bdc871 QQuickWindow::event()
#29 0x7fa9c1f6605c QApplicationPrivate::notify_helper()
#30 0x7fa9c1f6b516 QApplication::notify()
#31 0x7fa9c0a4e38b QCoreApplication::notifyInternal()
#32 0x7fa9c11ba4ac QGuiApplicationPrivate::processExposeEvent()
#33 0x7fa9c11bb21d QGuiApplicationPrivate::processWindowSystemEvent()
#34 0x7fa9c119ef08 QWindowSystemInterface::sendWindowSystemEvents()
#35 0x7fa9b8a8a200 <unknown>
#36 0x7fa9bf426197 g_main_context_dispatch
#37 0x7fa9bf4263f0 <unknown>
#38 0x7fa9bf42649c g_main_context_iteration
#39 0x7fa9c0aa47cf QEventDispatcherGlib::processEvents()
#40 0x7fa9c0a4bb4a QEventLoop::exec()
#41 0x7fa9c0a53bec QCoreApplication::exec()
#42 0x5607e9cf5e16 (/usr/bin/webbrowser-app+0x5607e9cf5e15)
#43 0x5607e9ceaa05 (/usr/bin/webbrowser-app+0x5607e9ceaa04)
#44 0x7fa9bfb7d830 __libc_start_main
#45 0x5607e9ceab69 (/usr/bin/webbrowser-app+0x5607e9ceab68)

Aborted (core dumped)
izak@behemoth:~$ [0100/000000.716361:ERROR:broker_posix.cc(41)] Invalid node channel message
```

---

