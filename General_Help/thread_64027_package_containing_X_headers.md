---
title: "package containing X headers"
date: 2005-09-09
forum: General Help
---

### Post by twelvegates on 2005-09-09
Which is the package that contains the headerfiles below /usr/X11R6/include?

---

### Post by amohanty on 2005-09-10
I think its called xorg-dev
Fre up synaptic and search for xorg.

HTH
AM

---

### Post by twelvegates on 2005-09-10
[QUOTE=amohanty]I think its called xorg-dev
Fre up synaptic and search for xorg.[/QUOTE]
Hm. As of xorg I have installed *xorg-common*, *xorg-driver-synaptics* and *xserver-xorg*.
Available are *xorg-driver-fglrx*, *xorg-driver-fglrx-dev* and *xserver-xorg-dbg*.
But there is nothing like *xorg-dev*.

---

### Post by twelvegates on 2005-09-10
There is a dummy package *xlibs-dev* containing several packages.
Installing xlibs-dev and it's dependencies populates /usr/X11R6/include.

---

