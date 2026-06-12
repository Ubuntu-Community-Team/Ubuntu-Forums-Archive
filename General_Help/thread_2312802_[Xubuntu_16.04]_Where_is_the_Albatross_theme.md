---
title: "[Xubuntu 16.04] Where is the Albatross theme?"
date: 2016-02-07
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-02-07
i  just took a look at 16.04 with a live usb and i noticed it was missing
in the past it has been part of the shimmer-themes package

---

### Post by mc4man on 2016-02-07
changelog
> shimmer-themes (2.1.0-0ubuntu1) xenial; urgency=medium

  * New theme snapshots (Greybird:fafd278, Numix:70b2565) (LP: #1535163)
    - Improved support for GTK 3.18
  * debian/control, Makefile:
    - Compile Numix sass assets
  * Drop unmaintained Albatross, Bluebirdm and Orion GTK themes

---

### Post by pqwoerituytrueiwoq on 2016-02-07
well that makes me sad, that was the only decent dark theme i have ever seen
know of any alternative themes?
i wonder if mate or cinnamon have any decent sensor panel items yet, and a alternative to the genmon-plugin

---

### Post by pqwoerituytrueiwoq on 2016-08-13
Seems i found a way to get it back, but it only works on gtk2 apps though
on this page
[https://launchpad.net/ubuntu/xenial/amd64/albatross-gtk-theme/2.0.2-0ubuntu1](https://launchpad.net/ubuntu/xenial/amd64/albatross-gtk-theme/2.0.2-0ubuntu1)
i found this deb file
[http://launchpadlibrarian.net/218484255/albatross-gtk-theme_2.0.2-0ubuntu1_all.deb](http://launchpadlibrarian.net/218484255/albatross-gtk-theme_2.0.2-0ubuntu1_all.deb)

gtk3 apps include catfish, gnome-calculator, gnome-disks, and software-center-gtk3
these apps will not match the rest of the system

edit: i think it will work on a few gtk3 apps after looking at the code
the theme is usable as of 16.04.1

---

