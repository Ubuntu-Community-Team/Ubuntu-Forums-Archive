---
title: "GDM/Autologin Questions"
date: 2007-12-17
forum: General Help
---

### Post by eapache on 2007-12-17
I'm running Xubuntu on a one-user system, and I'm trying to trim down boot time as much as possible.

What would happen if I set it to autologin and then disabled gdm from services-admin?

Basically, is it gdm that handles auto-login, or something else?

---

### Post by danwood76 on 2007-12-17
Dont disable GDM, it handles gnome login in general I believe, even with auto login.

---

### Post by DrMega on 2007-12-17
gdm is the Gnome display manger. If you disable that, you'll have no nice GUI if I understand correctly.

---

### Post by eapache on 2007-12-17
danwood76: Then is there a special way to autologin without it? Or some way to add a login/startx script to the boot process?

DrMega: But aren't I using XFCE as my gui? Or does XFCE depend on GDM?

---

### Post by strabes on 2007-12-17
xfce uses gdm.

---

### Post by danwood76 on 2007-12-17
[http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)

Im not sure, on older systems ive built with Xubuntu ive always just used the standard autologin script and left GDM running.

sorry I cant help

---

