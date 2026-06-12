---
title: "Trying to load Virtual Box so I can run WinXP"
date: 2008-05-13
forum: General Help
---

### Post by AmpersUK on 2008-05-13
I get the following error message but have no idea

a: Where to find the vboxdrv and
b: How to install it

I downloaded the program straight from "Add/Remove Programs" in Ubuntu.

I am new to Linux.

ERROR MESSAGE READS:
-------------------------------------------------------------------------------------------------------------------

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

-----------------------------------------------------------------------------------------------------------------------

Any help would be appreciated as I am tired of waiting for them to fix "Parallels Workstation" for 8.04.

---

### Post by Nythain on 2008-05-13
sudo apt-get install virtualbox-ose

think that should do teh trick

---

### Post by AmpersUK on 2008-05-13
No that isn't the problem.

I did what you suggest and it just told me there wasn't a newer program available to the one I had already installed on my machine.

The error message still shows.

---

### Post by Nythain on 2008-05-13
sorry then, thats all i got... when ya install the -ose version, it should install the -ose modules, at least it did for me 4 days ago

---

### Post by BlueSkyNIS on 2008-05-13
I just go to the [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") choose ubuntu, download .deb package and install it altogether with all dependencies automatically. ;)

---

