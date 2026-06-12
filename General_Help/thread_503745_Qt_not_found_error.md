---
title: "Qt not found error"
date: 2007-07-18
forum: General Help
---

### Post by bennyda on 2007-07-18
I am trying to compile an app in Feisty which requires Qt3. I still get an error saying "no valid Qt installation found". Any ideas? I have tried installing Qt3 a couple of time but still no luck.

Please help!!!!

Benny

---

### Post by az on 2007-07-18
You need th corresponding -dev package which contains the header files

 libqt3-mt-dev

Note:  The libqt3-headers  package now takes care of that for you, being a meta-package depending on the above package.
[http://packages.ubuntu.com/feisty/devel/libqt3-headers](http://packages.ubuntu.com/feisty/devel/libqt3-headers)

---

### Post by bennyda on 2007-07-19
thanks az. i did that but i still get the following error

...
checking for TIFFOpen in -ltiff... yes
checking for qmake... /usr/bin/qmake
configure: Checking for Qt >= 3...
configure: WARNING: TEST_QT3: QT3 is not installed or version of Qt is too old.
configure: Checking for Qt4...
configure: Qt4 not found.
configure: error: TEST_QT3/4: no usable Qt installation found. try --disable-qtgui

It runs fine until this point. Installing Qt4 doesn't help either.

---

### Post by az on 2007-07-19
> **bennyda said:**
> 
It runs fine until this point. Installing Qt4 doesn't help either.

Did you install the qt4 headers, too?

---

### Post by bennyda on 2007-07-20
yes. qt4 headers are installed

---

### Post by needtolookatascreenshot on 2007-07-20
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

