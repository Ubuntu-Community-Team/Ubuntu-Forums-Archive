---
title: "Errors when trying to install programs"
date: 2008-02-27
forum: General Help
---

### Post by Metaphysical on 2008-02-27
original, i tried to install Qalculate from the terminal. It didn't get all the way through the installation, and now if i try to install anything from terminal i get:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  qalculate
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/25.4kB of archives.
After unpacking 73.7kB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package qalculate.
(Reading database ... 136435 files and directories currently installed.)
Unpacking qalculate (from .../qalculate_0.9.4-2build1_all.deb) ...
Setting up gnuplot-nox (4.2.0-3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing gnuplot-nox (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnuplot-x11:
 gnuplot-x11 depends on gnuplot-nox (>= 4.2.0-3); however:
  Package gnuplot-nox is not configured yet.
dpkg: error processing gnuplot-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnuplot:
 gnuplot depends on gnuplot-nox (>= 4.2.0-3); however:
  Package gnuplot-nox is not configured yet.
 gnuplot depends on gnuplot-x11 (>= 4.2.0-3); however:
  Package gnuplot-x11 is not configured yet.
dpkg: error processing gnuplot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qalculate-gtk:
 qalculate-gtk depends on gnuplot; however:
  Package gnuplot is not configured yet.
dpkg: error processing qalculate-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qalculate:
 qalculate depends on qalculate-gtk; however:
  Package qalculate-gtk is not configured yet.
dpkg: error processing qalculate (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnuplot-nox
 gnuplot-x11
 gnuplot
 qalculate-gtk
 qalculate

```

how can i fix this?

---

### Post by Arwen on 2008-02-27
>  Package gnuplot is not configured yet.
It seems that you need to install gnuplot before installing calculate,but wait for a more precise answer(I don't really know what gnuplot is and why it may be needed.)

---

### Post by Metaphysical on 2008-02-27
well, i think i know why. I stopped dpkg-reconfigure xserver-xorg before it finished all the way. when i try to do dpkg-reconfigure xserver-xorg again i get 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

any solutions?

---

