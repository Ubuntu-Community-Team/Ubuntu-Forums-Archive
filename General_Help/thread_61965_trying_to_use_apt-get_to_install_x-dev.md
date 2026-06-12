---
title: "trying to use apt-get to install x-dev"
date: 2005-09-02
forum: General Help
---

### Post by kcthomas on 2005-09-02
i need the following libraries installed in order to install a touchpad driver

x-dev, libxll-dev, libxext-dev

root@KyleLinux:/ # sudo apt-get install x-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package x-dev

root@KyleLinux:/ # sudo apt-get install libxll-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxll-dev

root@KyleLinux:/ # sudo apt-get install libxext-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxext-dev

what am i doing wrong? thanks

---

### Post by DJ_Max on 2005-09-02
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by az on 2005-09-02
xlibs-dev (not x-dev)
[http://packages.ubuntu.com/hoary/oldlibs/xlibs-dev](http://packages.ubuntu.com/hoary/oldlibs/xlibs-dev)
[http://packages.ubuntu.com/hoary/libdevel/libxext-dev](http://packages.ubuntu.com/hoary/libdevel/libxext-dev)
[http://packages.ubuntu.com/hoary/libdevel/libx11-dev](http://packages.ubuntu.com/hoary/libdevel/libx11-dev)

---

