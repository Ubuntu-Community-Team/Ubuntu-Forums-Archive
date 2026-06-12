---
title: "Compilation error"
date: 2007-05-26
forum: General Help
---

### Post by niglch on 2007-05-26
I'm trying to compile TiLP2 in hopes that I will be able to use it with Ubuntu to connect with my TI-84+SE. Everything seems to be working after running ./configure until I get the following error:
```
checking for Qt... configure: error: Qt (>= Qt 3.0.2) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
```
I know this probably means I need to install a dependency, but I'm not exactly sure which ones. If I remember right, Qt is associated with KDE (yet I am running Gnome). Could anyone point me in the right direction?

...Compiling is such a pain...

---

### Post by yabbadabbadont on 2007-05-26
Use synaptic to search for libqt.  Then install the libqt*-dev version of whichever QT version you currently have installed.  For example, on Feisty there are both libqt3-mt-dev and libqt4-dev.

Edit: It doesn't matter that you are running Gnome, the program you are trying to build is a QT application.  You can run QT apps in Gnome just like you can run GTK+ apps in KDE.

---

