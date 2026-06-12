---
title: "Ubuntu 12.04 and Autodesk maya 2014"
date: 2013-09-17
forum: General Help
---

### Post by akimb0 on 2013-09-17
Hello,

i got some trouble with Autodesk Maya 2014. I know its running on Ubuntu but for me it seems its not that easy :-)
The installation and activation was not that hard but now im stocked in a error message right after the splash screen which i can't interpret.

```
maya


maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/aki.20130917.1315.ma
Segmentation fault (core dumped)
```

So i enabled the DEBUG and started maya again

```
export MAYA_DEBUG_ENABLE_CRASH_REPORTING=1
maya


maya encountered a fatal error

Signal: 11 (Unknown Signal)
Stack trace:
  [B]/lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7f27ebde64a0]
  xcb_glx_get_string_string_length
  /usr/lib/x86_64-linux-gnu/libGL.so(+0x404d4) [0x7f27c782f4d4]
  /usr/lib/x86_64-linux-gnu/libGL.so(+0x3df2c) [0x7f27c782cf2c][/B]
  GLFunctionTable::populate()
  GLStartupContext::GLStartupContext(WindowWrapper const&, __GLXcontextRec*)
  OGLRenderBackEnd::createResourceContext(WindowWrapper const*, void*)
  T3dView::updateViewingParameters()
  TidleRefreshCmd::refreshBaseRender(T3dView*, bool, bool, TdisplayAppearance, bool, bool, bool)
  TidleRefreshCmd::refresh(T3dView*, TdisplayAppearance, bool, bool, bool, bool, TrefreshType, bool, bool)
  TtoolRefresh::refreshFast(T3dView*, TrefreshType)
  T3dView::doUpdate(Tevent const&)
  T3dPort::resize(Trect const&)
  QmayaGLWidget::resizeGL(int, int)
  Qmaya3dWidget::resizeEvent(QResizeEvent*)
  QWidget::event(QEvent*)
  QmayaGLWidget::event(QEvent*)
  QApplicationPrivate::notify_helper(QObject*, QEvent*)
  QApplication::notify(QObject*, QEvent*)
  QmayaApplication::notify(QObject*, QEvent*)
  QCoreApplication::notifyInternal(QObject*, QEvent*)
  QWidgetPrivate::sendPendingMoveAndResizeEvents(bool, bool)
  QWidgetPrivate::show_helper()
  QWidgetPrivate::showChildren(bool)
  QWidgetPrivate::show_helper()
  QWidget::setVisible(bool)
  QWidgetPrivate::showChildren(bool)
  QWidgetPrivate::show_helper()
  QWidget::setVisible(bool)
  QWidgetPrivate::showChildren(bool)
  QWidgetPrivate::show_helper()
  QWidgetPrivate::showChildren(bool)
  QWidgetPrivate::show_helper()
  QWidget::setVisible(bool)
  QWidgetPrivate::showChildren(bool)
  QWidgetPrivate::show_helper()
  QWidget::setVisible(bool)
  TiceControlBaseCmd::doEditFlags()
  TelfLayoutBaseCmd::doEditFlags()
  TelfPaneLayoutCmd::doEditFlags()

Fatal Error. Attempting to save in /usr/tmp/aki.20130917.1315.ma
Segmentation fault (core dumped)
```

Where ```
/lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7f27ebde64a0]
  xcb_glx_get_string_string_length
```

and ```
/usr/lib/x86_64-linux-gnu/libGL.so(+0x404d4) [0x7f27c782f4d4]
  /usr/lib/x86_64-linux-gnu/libGL.so(+0x3df2c) [0x7f27c782cf2c]
```

seems to be the problem...

Im not able to interpret both messages exactly. The only thing i know is that it has be something with my GPU-Driver and need some help here :(

Some informations about my system below:

```
lspci
07:00.0 VGA compatible controller: NVIDIA Corporation GK104 **[GeForce GTX 690]** (rev a1)
07:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
08:00.0 3D controller: NVIDIA Corporation GK104 [GeForce GTX 690] (rev a1)
08:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)

```

```
uname -r
**3.5.0-40-generic**
```

```
dpkg -l | grep nvidia
[B]ii  nvidia-319                                319.32-0ubuntu0.0.1                                NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-319-dev                            319.32-0ubuntu0.0.1                                NVIDIA binary Xorg driver development files
ii  nvidia-common                             1:0.2.44.2                                         Find obsolete NVIDIA drivers[/B]
rc  nvidia-current                            304.88-0ubuntu0.0.2                                NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-current-updates                    304.88-0ubuntu0.0.1                                NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-experimental-310                   310.14-0ubuntu0.3                                  Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
**ii  nvidia-persistenced                       319.23-0ubuntu1~xedgers~precise1                   Load the NVIDIA kernel driver and create device files**
rc  nvidia-settings                           304.88-0ubuntu0.0.2                                Tool of configuring the NVIDIA graphics driver
**ii  nvidia-settings-319                       319.32-0ubuntu0.0.1                                Tool for configuring the NVIDIA graphics driver**
rc  nvidia-settings-experimental-310          310.14-0ubuntu0.1                                  Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-updates                   304.88-0ubuntu0.0.2                                Tool of configuring the NVIDIA graphics driver
```

So as you can see im using the **319.32 driver** currently without any issues.

What else did you need?

---

### Post by akimb0 on 2013-09-19
Nobody an idea of what is going wrong here??

---

### Post by ragtag on 2013-09-22
If I'm not mistaken /usr/lib/x86_64-linux-gnu/libGL.so is a symlink to /usr/lib/x86_64-linux-gnu/mesa/libGL.so and is installed along with libgl1-mesa-dev. Accodring to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/943162"), it's an error an overrides the alternatives system in Ubuntu.

On 12.04 with Maya 2013 I've simply deleted /usr/lib/x86_64-linux-gnu/libGL.so without any adverse effect after a week or so of use, though admitedly I haven't compiled anything using libgl1-mesa-dev, so I'm not sure if deleting libgl.so will cause issues there.

Also check out [this thread]("/usr/lib/x86_64-linux-gnu/libGL.s"), the post about preloading libjpeg. By default Maya 2013 crashes when you try to access jpeg images.

---

### Post by ragtag on 2013-09-24
Just a quick reply. I've found that if I try to compile software that needs ligbl1-mesa-dev (e.g. OpenColorIO, Krita and more), I need that symlink back. A quick "sudo apt-get --reinstall install libgl1-mesa-dev" will do the trick.

---

