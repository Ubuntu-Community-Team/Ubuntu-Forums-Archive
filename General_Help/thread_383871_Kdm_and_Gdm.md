---
title: "Kdm and Gdm"
date: 2007-03-13
forum: General Help
---

### Post by Deviltongue on 2007-03-13
how do I swap the login the from KDM to GDM?

---

### Post by zvacet on 2007-03-14
On the login screen you go to sessions and choose one you like.

---

### Post by scxtt on 2007-03-14
no, you edit /etc/X11/default-display-manager w/ the FULL PATH to the display manager you want to use ... of course this only works w/ DMs that are installed ...

:> whereis xdm
xdm: **/usr/bin/xdm** /usr/X11R6/bin/xdm /usr/bin/X11/xdm /usr/share/man/man1/xdm.1.gz

:> whereis kdm
kdm: **/usr/bin/kdm** /usr/X11R6/bin/kdm /usr/bin/X11/kdm

---

### Post by Deviltongue on 2007-03-14
okay but where is GDM?

---

### Post by Arby on 2007-03-14
if you type 'whereis gdm' in a terminal your system will tell you where it is.

Given that xdm, the xfce display manager, and kdm, the kde display manager are both in /usr/bin it's a fair bet that gdm will be there as well. But check first with the whereis command.

---

### Post by scxtt on 2007-03-15
xdm isn't specifc to XFCE ... and i think gdm is in /usr/sbin, but as was stated "whereis gdm" will tell you ...

---

