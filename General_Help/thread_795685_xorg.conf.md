---
title: "xorg.conf"
date: 2008-05-15
forum: General Help
---

### Post by zieglerj on 2008-05-15
Where is my xorg.conf file and how do I configure it?

---

### Post by mikewhatever on 2008-05-15
> **zieglerj said:**
> Where is my xorg.conf file and how do I configure it?

xorg is in /etc/X11. Use <gksudo nautilus /etc/X11/xorg.conf> to edit it, but make a backup copy first: <sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup>.

---

### Post by tommyhakinen on 2008-05-16
> **zieglerj said:**
> Where is my xorg.conf file and how do I configure it?

it is found at /etc/X11/xorg.conf.

Before making any changes, please backup it up first:

> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup


In order to edit and save the changes, you need to be root

> 
sudo gedit /etc/X11/xorg.conf


Enter your password when prompted

---

