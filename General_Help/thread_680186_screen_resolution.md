---
title: "screen resolution"
date: 2008-01-27
forum: General Help
---

### Post by mpgarate on 2008-01-27
ubuntu never liked my graphics I guess. It picks the wrong, way too low screen resolution by default, until I unstall the nvidia restricted drivers. Suse gets it just fine.. but i prefer ubuntu. does suse enable these drivers by default? Will this problem ever be fixed? Ive had it since 6.06

---

### Post by taurus on 2008-01-27
What's wrong with going into System -> Administration -> Restricted Drivers Manager and install a driver for your nvidia card?  Once you do it, you don't have to do it again.

---

### Post by mpgarate on 2008-01-27
true, but its nearly impossible to install with a screen resolution of 640 by 480

I do like to try out and use livecds too, like trying out kde4 etc

---

### Post by taurus on 2008-01-27
If you want to install it from a terminal, you can run

```
sudo apt-get update
sudo apt-get install nvidia-glx-new
```
Then, just edit /etc/X11/xorg.conf and replace nv with nvidia in the Driver option.

---

### Post by Majorix on 2008-01-27
Run in recovery mode (an option during the start). There run
```
dpkg-reconfigure -phigh xserver-xorg
```
and choose nvidia for driver (if that's not an option you will have to change this manually a suggested above) and then type "reboot" without the quotes to reboot the machine in normal mode.

---

