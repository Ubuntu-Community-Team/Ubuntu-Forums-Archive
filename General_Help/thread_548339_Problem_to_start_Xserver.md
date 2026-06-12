---
title: "Problem to start Xserver??"
date: 2007-09-11
forum: General Help
---

### Post by MrGando on 2007-09-11
Hi guys, I installed Ubuntu server, 
did a 

sudo apt-get install gnome gdm



but I can't get the xserver to load, so no gnome

[IMG]http://img502.imageshack.us/img502/7438/xserverzo1.png[/IMG]

Help please :)

---

### Post by MrGando on 2007-09-11
so I did a reinstall of xserver now

like

sudo apt-get remove xserver-xorg && sudo apt-get install xserver-xorg -y

now I get this:

[IMG]http://img292.imageshack.us/img292/8231/x11gy4.png[/IMG]

---

### Post by RedSquirrel on 2007-09-11
I would recommend installing the** xorg** package:

```
sudo apt-get install xorg
```

EDIT: Once it's installed, I would do this as well to configure Xorg:
```
sudo dpkg-reconfigure xserver-xorg
```

By the way, if you're going to use gdm, try starting it like this:

```
sudo /etc/init.d/gdm start
```

---

