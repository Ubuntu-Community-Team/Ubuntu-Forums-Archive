---
title: "Kernel 2.6.24-18-generic and Virtual Box"
date: 2008-06-06
forum: General Help
---

### Post by fmartinez on 2008-06-06
Just wanted to send this out to all the Virtual box users: I just recently upgraded to this version of this kernel (2.6.24.18-generic). When I saw the upgrade of course I made sure that Vdrivers with Xorg and all that good stuff were included with the upgrade, but that was the only thing. 
I completely forgot the Vbox-ose module. I went ahead and upgraded regardless... WHOOPS! 
I finally remembered after the reboot. So i thought Ok let's go find the latest VBox module through Synaptic... OOps the latest is 2.6.24.17. 
Finally I rolled back to the 2.6.24.17 kernel version and installed the same for VBox. I confirmed the Vdrivers where still there and everything seems ok for now. 
This is just a word of caution before installing these latest updates! 
Good Luck!

---

### Post by ibuclaw on 2008-06-06
Is this the VirtualBox OSE?

If your having problems, get the [official binary version.]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

Then run the command
```
sudo /etc/init.d/vboxdrv setup
```
To compile the vbox modules against the 2.6.24-18 kernel.


Regards
Iain

---

### Post by fmartinez on 2008-06-06
no I'm not having any problems anymore... just wanted to send this out a and FYI... thanks for the reply.

---

