---
title: "Disabling Lubuntu Desktop"
date: 2018-11-29
forum: General Help
---

### Post by horrido on 2018-11-29
I've installed Ubuntu Server 18.04 and Lubuntu-desktop. However, I would like to disable Lubuntu desktop on boot up and only start it manually as needed. I am unable to do this. I've tried:

sudo service lightdm stop

/etc/init.d/lightdm stop

But on boot-up, I always get the Lubuntu login screen. Is there no way to do this (easily)?

---

### Post by deadflowr on 2018-11-29
Try
```
sudo systemctl disable lightdm
```
More on systemctl:
[https://www.freedesktop.org/software/systemd/man/systemctl.html]("https://www.freedesktop.org/software/systemd/man/systemctl.html")

---

### Post by horrido on 2018-11-29
Then, how do I start LXDE manually (without rebooting)?

---

### Post by #&amp;thj^% on 2018-11-29
This will prevent the service from starting at "boot":

```
sudo systemctl disable lightdm.service
```

To start the GUI (lightdm), Its as simple as starting the service 
```
sudo systemctl start lightdm.service
```

---

### Post by deadflowr on 2018-11-29
You don't need lightdm to run lxde.
Just add the line
```
exec startlxde
```
to your ~/.xinitrc file
then to run just enter 
```
startx
```
in the console prompt.

if you don't have an xinitrc file, then make it.
This file is your file, so do not run with sudo or as root.
(Reason not to run it as root is that will make it root owned and  you don't need or want that)

For references:
[https://wiki.archlinux.org/index.php/LXDE#Console]("https://wiki.archlinux.org/index.php/LXDE#Console")
[http://lxde.sourceforge.net/install.html]("http://lxde.sourceforge.net/install.html")

---

### Post by horrido on 2018-11-29
Nope, this does not work. In fact, it causes a logout, probably something crashed.

---

