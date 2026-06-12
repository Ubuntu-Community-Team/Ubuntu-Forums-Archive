---
title: "qmake for qt4"
date: 2007-06-27
forum: General Help
---

### Post by stephaneeybert on 2007-06-27
Dear all,

I have qt4, the core and dev.

root@stephane-laptop:/home/stephane# apt-get install libqt4-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt4-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 138 not upgraded.
root@stephane-laptop:/home/stephane# apt-get install libqt4-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt4-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 138 not upgraded.

But my qmake version is still 3.

root@stephane-laptop:/home/stephane# qmake -v
Qmake version: 1.07a (Qt 3.3.6)
Qmake is free software from Trolltech AS.

And I need to have the Qt 4.2 or above.

What can I do..?

Thanks

Stephane

---

### Post by mr_ed on 2007-06-27
Did you install qt4-dev-tools?

---

