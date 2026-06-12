---
title: "Unable To Connect to Internet On Lubuntu Live CD"
date: 2015-10-28
forum: General Help
---

### Post by quaesitor2 on 2015-10-28
I booted Lubuntu live on my macbook air os 10.6.8 snow leopard. The Lubuntu disk is lubuntu-15.4-desktop-i386.

I am unable to use the internet on the disk can anyone help me?

---

### Post by Vladlenin5000 on 2015-10-28
Some WiFi devices have no native support therefore what's usually recommended is to install and troubleshoot from there, in the installed OS.
If you have no intention of installing it for real and/or need some kind of portable installer media where you can make changes then you must use a USB flash drive (with persistence) instead of optical disks. You can't install in a CD or DVD, obviously.

---

### Post by Bucky Ball on 2015-10-28
Continuing from Vladlenin5000's post. Some wireless won't work on anything but a full install (not a Live session). 

Plug in with an ethernet cable on the Live session, open a terminal and input this command:

```
sudo lshw -C network
```

That will tell us the wireless card you have and give us a good idea of your chances of wireless success with a full install. 

With an ethernet cable plugged in, you can also do an update (use Software Updater or 'sudo apt-get update' in a terminal) and then check 'Additional Drivers'. This may show a driver which you can probably install, but all will be lost on reboot as you are on a Live boot. For things to stick you will need a persistence install, as suggested by Vladlenin5000, to USB, or a full install to hard drive partitions.

[Universal USB Installer]("www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") gives you the option to install with persistence.

---

