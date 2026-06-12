---
title: "Installing QT headers and libraries"
date: 2004-11-06
forum: General Help
---

### Post by stodge on 2004-11-06
Ok I'm confused. I installed KDE and KDevelop using the instructions on this site. Now I'm trying to install the QT includes. Synaptic shows libqt3c102 as being installed, but it only shows libqt3-dev for the dev package. Are these the same version of QT? If not, will I screw up the dependencies by installing this?

Thanks

---

### Post by stodge on 2004-11-06
I just can't get round this:

checking for Qt... configure: error: Qt (>= Qt 3.1.0) (library qt-mt) not found.

Even though I have the QT headers and libraries installed.

---

### Post by p!=f on 2004-11-06
```

  * 01:17:41 * pef @ agonicus *
 [~/src] > apt-cache search qt-mt
 libqt3-dev - Qt development files
 libqt3-headers - Qt3 header files
 libqt3-mt-dev - Qt development files (Threaded)
 libqt3c102-mt - Qt GUI Library (Threaded runtime version), Version 3
 
```
 
 So you probably want to install libqt3-mt-dev and libqt3c102-mt.

---

