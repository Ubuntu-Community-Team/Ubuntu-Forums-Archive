---
title: "auto startup applications"
date: 2007-05-31
forum: General Help
---

### Post by molsen on 2007-05-31
how do i set an application to start up when i log in to xubuntu 7.04?  i.e. firestarter firewall

---

### Post by digitalbenji on 2007-05-31
add an entry for it in system-preferences-sessions

---

### Post by molsen on 2007-05-31
excellent, thank you!

---

### Post by ajgreeny on 2007-05-31
But remember that for firestarter in particular, you do not need it running just to have a firewall in ubuntu.  Firestarter is simply the gui to make changes to iptables, the firewall itself, which is running all the time by default.  Also bear in mind that unless you open a port on your machine (for example by opening firefox) there are none open on ubuntu.

---

### Post by molsen on 2007-05-31
ohhhhhhhh.  this i did not know.  thanks for the heads up.  i'm so new to this stuff it's sickening

---

### Post by gerdt on 2007-11-12
There is no system-preferences-sessions in my Xubuntu Gutsy 7.10
I don't know if its my fault it isn't there, or if its Gutsy...

Does anyone know how I can easily/graphically put certain programs in my Xubuntu startup?
In this case I want to auto-start google-desktop, but I might also want to auto-start some other programs.

---

### Post by QwUo173Hy on 2008-03-15
run this from the terminal:

xfce4-autostart-editor

---

### Post by strabes on 2008-03-15
> **gerdt said:**
> There is no system-preferences-sessions in my Xubuntu Gutsy 7.10
I don't know if its my fault it isn't there, or if its Gutsy...

Xubuntu doesn't have the same menu system as ubuntu because they use different desktop environments (xfce4 and GNOME, respectively).

---

