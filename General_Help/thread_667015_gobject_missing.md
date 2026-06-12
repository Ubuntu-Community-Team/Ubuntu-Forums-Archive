---
title: "gobject missing?"
date: 2008-01-13
forum: General Help
---

### Post by Heftiger on 2008-01-13
I'm trying to install a budget program and it says it requires gobject. Even though it's installed, it's not working. Heres the code:

> nick@ubuntu:~/Desktop/myBudget-0.60$ ./install.py /path/to/prefix
Finding all installed modules...
Checking for gobject...
gobject not installed. You need to install this for MyBudget
Checking for gtk...
gtk OK
Checking for libglade...
libglade OK
Checking for gconf...
gconf OK
 Can not install MyBudget, please supply th needed modules 

However, when I try and install gobject, it says it's already installed:

> nick@ubuntu:~/Desktop/myBudget-0.60$ sudo apt-get install python-gobject
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gobject is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

---

### Post by erpo on 2008-01-14
Have you searched the project web site or mailing list for myBudget? Have you requested that someone involved with the project make an Ubuntu package?

---

### Post by Seisen on 2008-01-14
Try installing ```
python-gobject-dev
``` package and then see if it will compile.

---

