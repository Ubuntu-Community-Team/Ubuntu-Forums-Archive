---
title: "kde apps on gnome"
date: 2008-05-11
forum: General Help
---

### Post by penquin on 2008-05-11
I can't seem to get my k9copy, k3b, and amarok to work on gnome now that I upgraded to hardy.  Any suggestions?

---

### Post by y-lee on 2008-05-11
I don't know what the problem is but we need more information than that. Start these programs in a terminal and post any error output here. Also note sometimes programs that stop working can be fixed simply by reinstalling them, you might want to try that first. Upgrading to Hardy might have somehow messed up your KDE libraries :confused:

---

### Post by penquin on 2008-05-12
amarok: symbol lookup error: /usr/lib/libkdecore.so.4: undefined symbol: stat64

---

### Post by cprofitt on 2008-05-12
Sounds like a library for KDE is missing... have you tried uninstalling some of the apps and reinstalling them? or checking if the apps have not been upgraded?

check for kdelibs4c2a (>=4:3.5.8-1) and libqt3-mt (3:3.3.8-b)

---

### Post by penquin on 2008-05-13
I have done both.  I have also tried to install libs that could be related to it.

---

