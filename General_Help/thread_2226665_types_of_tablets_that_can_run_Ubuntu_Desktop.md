---
title: "types of tablets that can run Ubuntu Desktop"
date: 2014-05-28
forum: General Help
---

### Post by PhartSmellah on 2014-05-28
*(I posted this under Hardware as well, but no answer... maybe wrong sub-forum?)*


Lately you can see all kinds of laptop/tablet/pc hybrids: Laptop convertibles, Tablet PCs, Tablets. Also, they run either ARM, Atom or full Core i3/5/7 processors. Some use GRUB, others use EUFI.
I was wondering on which of these can I install ***Ubuntu Desktop edition*** (currently 14.04 LTS). I'd like to be able to:

[LIST=1]
[*]Boot up from the USB drive (probably some keyboard shortcut)
[*]Install Ubuntu with the regular image
[*]Touch support
[*]Optionally recognize tablet keys and orientation
[/LIST]
I'd like to know which architectures (Core/Atom/ARM) and bootloaders (GRUB/EUFI) support Ubuntu Desktop.
Can I install Ubuntu Desktop on any tablet, as long as it runs Core i3/5/7, for eg.?

---

### Post by grahammechanical on 2014-05-28
Forgive me but there are some things that we must be clear in our minds about.

UEFI is not a boot loader but a boot system like BIOS. Grub is not a boot system but a boot loader. I would be very much surprised to find a tablet on the market that has Grub but not a Linux distribution being pre-installed.

The "regular" Ubuntu ISO image will not work with ARM CPUs. We need a Ubuntu ISO image that has been ported to ARM. And there are many more ARM CPUs in devices than there are ports of Ubuntu to the ARM CPUs in those devices. 

The latest desktop version of Ubuntu is 14.04 and that does not come with "Touch" support because Ubuntu Touch is the name given to the user interface being developed for phones and tablets. But Ubuntu 14.04 desktop is compliant with touch screen monitors.

Boot from a USB port would be a function of the hardware of the device and the boot system used with it (UEFI or something else). Recognition of tablets keys and orientation would be dependant on Ubuntu being ported to that particular device. 

Please do not expect what cannot be given. What you are seeking is very much an experiment. You could be disappointed in the results.

[https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)

[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

[https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch)

Regards.

---

### Post by Bashing-om on 2014-05-28
PhartSmellah; Hi !

In addition to grahammechanical's response;
If you have a strong interest in this field, may I suggest that you join the discussions @
[http://discourse.ubuntu.com/](http://discourse.ubuntu.com/)
for the latest info on the emerging mobile device technologies.

[INDENT][INDENT]to be in-the-know
[/INDENT][/INDENT]

---

### Post by PhartSmellah on 2014-05-30
> **grahammechanical said:**
> 
The "regular" Ubuntu ISO image will not work with ARM CPUs. We need a Ubuntu ISO image that has been ported to ARM. And there are many more ARM CPUs in devices than there are ports of Ubuntu to the ARM CPUs in those devices. 

The latest desktop version of Ubuntu is 14.04 and that does not come with "Touch" support because Ubuntu Touch is the name given to the user interface being developed for phones and tablets. But Ubuntu 14.04 desktop is compliant with touch screen monitors.


Does that mean that the Desktop ISO **will** work with any Core/Atom processor?
(meaning - touch-enabled laptops, tablet/laptop convertibles)

---

