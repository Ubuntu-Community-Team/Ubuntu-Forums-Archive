---
title: "Setting up QT5 SDK and QT Creator correctly"
date: 2013-09-20
forum: General Help
---

### Post by Nunyah on 2013-09-20
Hi all,

I've been trying to install the QT5 SDK by following the 2nd part of this guide: [http://www.wikihow.com/Install-Qt-SDK-on-Ubuntu-Linux](http://www.wikihow.com/Install-Qt-SDK-on-Ubuntu-Linux)

At the end of the guide where I test to see if things are as expected:
```
'which qmake' /usr/bin/qmake rather than /opt/Qt5.1.1/Qt5.1.1/gcc/bin/qmake
```
'qmake -version' shows 4.8.3 rather than 5.1.1.

So a previous installation of the SDK is still configured as 'the main' version.

Would any of you know how I could change it?

---

### Post by steeldriver on 2013-09-20
It sounds like you have a previous QT4 installation - you should be able to switch between them using either the QT_SELECT environment variable, or (if you are using Cmake) by passing the -DQT_QMAKE_EXECUTABLE=xxx parameter

See similar thread here --> [http://ubuntuforums.org/showthread.php?t=2168435](http://ubuntuforums.org/showthread.php?t=2168435)

SOURCE: [https://wiki.archlinux.org/index.php/KDE_Package_Guidelines](https://wiki.archlinux.org/index.php/KDE_Package_Guidelines)

---

### Post by Nunyah on 2013-09-30
Sorry for the late reply. I've been away for some days.

While looking at it again, I noticed I had a typo of '/opt/Qt5.1.1/Qt5.1.1/gcc/bin/qmake' rather than '/opt/Qt5.1.1/Qt5.1.1/**gcc_64**/bin/qmake'. The correct qmake is now shown as default.

I also had to tell cmake where it could find Qt5Core by '-DCMAKE_PREFIX_PATH=/opt/Qt5.1.1/5.1.1/gcc_64/lib/cmake'.

Thank you for the response, steeldriver!

---

