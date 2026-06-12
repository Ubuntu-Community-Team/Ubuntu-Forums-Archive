---
title: "Freezes resolve on my Gutsy installation"
date: 2007-10-27
forum: General Help
---

### Post by zippy028 on 2007-10-27
My System;
ASUS M2N SLI Mobo with Nforce 570 Chipset
AMD 64X2 3800 CPU
1GB corsair DDR2
Western Digital SATA HDD
Nvidia 7300 LE

  I believe the hardware I listed is part of the problem with the latest drivers.
I removed all of the "nvidia-glx-new" drivers from my system and all kernel sources and or modules relating to the "new" drivers. 

What I have installed for nvidia drivers via synaptic
"linux-restricted-modules-2.6.22.4-14.9"
"nvidia-kernel-2.6.22-14-generic"
"nvidialinux-restricted-modules-2.6.22.4-14.9"
"nvidia-kernel-common"
"nvidia-kernel-source"
not sure if I need all of the above but 3D acceleration is working with compiz set to extra effects.

I completely removed the restricted driver manager pkgs. via synaptic
"restricted-manager"
"restricted-manager-core"

Then I downloaded [version 100.14.09](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)  from the nvidia driver archive. I then executed ctl-alt-F2 logged in and stopped gdm with the following command ```
sudo /etc/init.d/gdm stop
```and followed the instructions for installing the driver which is to execute this command ```
sudo sh NVIDIA-Linux-x86-100.14.09-pkg1-run
```from the directory I downloaded them to, in my case my /home dir. The driver installer should do the work for you from this point after it builds a kernel module or interface not sure what it is called. I selected the option to let the installer configure my xorg.conf file and then issued the command ```
sudo /etc/init.d/gdm start
``````
ctl-alt-F7
```and for the last few hours I have been running Firefox watching videos on youtube and playing tux racer all at the same time with no crashes or freezes to speak of.
YMMV,

John

---

### Post by komsas on 2007-11-07
I cant find nvidia-kernel-2.6.22-14-generic where it can be?

---

### Post by stldirty on 2007-11-16
my freezing has drastically decreased after following this.  thanks a lot man.

---

### Post by Ferux on 2007-12-15
omg, this works GREAT! Everybody suffering from the Nvidia problem (and that are a lot of people) should check this out!

I have only one problem: after rebooting, the new driver doesn't load automatically, so I have to install it everytime I login :(

If you have an idea to solve this problem, feel free...

---

### Post by andersm4 on 2008-01-03
This seems to have solved my freezing issues as well, but like the above post, I have to re-install these drivers every time I reboot.  Is there a solution for this?

Also, I currently have desktop effects disabled, and if I try to enable them i get an error message telling me to install the latest Nvidia drivers.  Any thoughts?

---

