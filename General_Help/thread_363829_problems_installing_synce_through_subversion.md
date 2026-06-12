---
title: "problems installing synce through subversion"
date: 2007-02-17
forum: General Help
---

### Post by commonplace on 2007-02-17
I'm trying to install SynCE through Subversion using the instructions on [the wiki]("http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_%28usb-rndis-lite%29"). I'm at the step of 'connecting your device' and I'm going to be using USB and not Bluetooth (since I don't have BT on my computer).

I'm at the part where I need to compile usb-rndis-lite, and it says: "You need to have CONFIG_USB_NET_CDCETHER compiled either into the kernel, or as a module, in your kernel config. Located in Device Drivers -> USB support -> USB Gadget support -> Ethernet Gadget"

I didn't know what that meant or how to check, so I proceeded anyway, and it failed, naturally, saying I didn't have cdcether (amongst other things). I can't find any instructions on how to install cdcether, how to compile it into my kernel or as a module (not sure what the difference is nor what would be best/easiest), etc.

Here's what it says:

```
$ sudo ./clean.sh
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/kevin/Downloads/synce/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
ERROR: Module rndis_host does not exist in /proc/modules
ERROR: Module cdc_ether does not exist in /proc/modules
ERROR: Module usbnet does not exist in /proc/modules
```

What's my next step? The wiki says it's "located in Device Drivers -> USB support -> USB Gadget support -> Ethernet Gadget", but I don't know to what they're referring. Anyone? Thanks!!

/Kevin

---

### Post by ombra32 on 2007-03-23
I have the same problem......anybody can help us? I'm a newbie...

---

### Post by mrming on 2007-04-14
I've been googling for weeks trying to solve this one. Can anyone help? :(

---

### Post by MikeEvans on 2007-05-28
Same problem.  I've been trying to get Synce working for weeks.  I was able to install usb-rndis-lite a few times and got to the point when my device is detected when I plug it in, but then i had trouble with gnome-vfs.  But when i was working on that issue my machine stopped detecting my PDA.  I went to reinstall usb-rndis-lite but im getting this error.

---

### Post by wersdaluv on 2007-05-29
I Googled "synce 0.10 deb" and got [this]("http://www.nabble.com/SynCE-0.10.0-Debian-Packages-t3773838.html"). Add 
```
deb http://jonnylamb.com debian/
``` in your sources.list if you want to install it using Synaptic or apt.

---

### Post by edmondt on 2007-06-06
Looks like its getting there... it woule be great if wm5 is supported right out of the box :)

---

