---
title: "Crash HELP on UBUNTU GDM PLEASE HELP..."
date: 2008-05-27
forum: General Help
---

### Post by ravindukelum on 2008-05-27
:confused:I got compaq presario v3614AU lap top and installed xp and ubuntu 7.10 on dual boot yesterday download all ubuntu updat and opted to instal all updat and I saw dialog box saying configuring then stuck the machine then I restarted the ubuntu and after boot screenI saw somthing sayng x server is not configured fatal error here some part of :
[442.024000]bcm 43xx :FATAL ERROR: BCM 43xx_IRQ_XMIT_ERROR

NVIDIA:No matching device section for instance(BUSID PCI:0:13) FOUND
(11)MODULE ALREADY BUILT IN 
FATAL:Error running installed command for nvidia
(EE) NVIDIA(0):faied to load the nvidia kernel module.
screens found, but none have a usable configuration
fatal server error"
no screen found.

I got NVIDIA nFOrce 7150m CHIPSET on my AP TOP 

PLEASE HELP TO GET BACK MY GNOME DESKTOP BACK I DON'T HAVE ANY KNOWLEDGE ABOUT CONFIGURING X SERVER PLEASE IS THERE ANY COMFORTABE WAY TO GET GDM BACK...:popcorn:

---

### Post by Riffer on 2008-05-27
I think what has happened is that you have updated your kernel, and your nVidia module needs to be updated as well.

Does a command line show up? If so type in

> sudo dpkg-reconfigure -phigh xserver-xorg 

This command reverts the system back to a basic driver so you can at least boot back into gnome.

Also if it is an updated kernel you can boot into your older kernel.  When you first boot up and the grub menu appears go to the Ubuntu 2nd from the top.  Boot from there, hopefully you'll again get back into gnome.

good luck

---

### Post by ravindukelum on 2008-05-27
I tried all things but it doesn't work yet please help me to solve this

---

### Post by Riffer on 2008-05-27
Try booting in "Safe Graphics Mode".  See if that works.  If it does use envyng and remove all nVidia drivers.  Reboot and see if that works.

---

