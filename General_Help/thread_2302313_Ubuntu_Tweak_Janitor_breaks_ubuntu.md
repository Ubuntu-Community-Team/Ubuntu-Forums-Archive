---
title: "Ubuntu Tweak Janitor breaks ubuntu"
date: 2015-11-09
forum: General Help
---

### Post by pouldney on 2015-11-09
Acer Aspire XC-605  ubuntu 14.04
   used Ubuntu Tweak Janitor  to remove most  old  kernels from 14.04
 pluss all "Package config" and all "Uneeded packages"
     This broke ubuntu. Ubuntu would boot but no greeter/login screen came up
  just a blank screen with cursor
  I tried booting old kernels in grub with same result Then tried  recovery mode in grub menue
     The boot ended with "initctl: Event failed" message.
  I was able to log in. I tried startx but got failure - cannot stat /etc/x11/x (No such file or directory)
    
             Used these commands
sudo apt-get update && apt-get upgrade
sudo apt-get install -reinstall xserver-xorg
sudo apt-get install -reinstall gdm gnome-desktop-environment xorg

      Then I was able to log in and when I re booted ubuntu was back as normal

---

### Post by egeezer on 2015-11-09
There are much safer ways to remove old kernels.  If you have Synaptic, just do a Completely Remove on the old kernel images (save the previous one along with the current one for safety) and on the headers.  If you don't have Synaptic, use either
```
sudo apt-get install synaptic
```

or go straight to the source and use
```
 $ sudo apt-get purge linux-image-3.19.0-15
$ sudo apt-get purge linux-headers-3.19.0-15
  
```
for just one, or
```
 $ sudo apt-get purge linux-image-3.19.0-{18,20,21,25}
$ sudo apt-get purge linux-headers-3.19.0-{18,20,21,25}
  
```
for several.

---

### Post by grahammechanical on 2015-11-09
> Then I was able to log in and when I re booted ubuntu was back as normal

Close, but not close enough

> sudo apt-get install -reinstall gdm gnome-desktop-environment xorg

Ubuntu does not use GDM. Ubuntu uses LightDM, Unity and the ubuntu-desktop. But it got you a working system.

Regards.

---

### Post by mörgæs on 2015-11-10
Next time just run ```
sudo apt-get autoremove
``` and it will delete all kernels except the two latest.

---

### Post by mastablasta on 2015-11-10
known issue with janitor cleaning too many things... yet another half done "app"

---

### Post by vasa1 on 2015-11-10
> **mastablasta said:**
> known issue with janitor cleaning too many things... yet another half done "app"+1. I seem to remember being cautioned about using janitor without being very, very careful about what it would do.

---

