---
title: "Trouble insalling Ubuntu to USB Key"
date: 2008-01-08
forum: General Help
---

### Post by icanrule on 2008-01-08
I just installed Ubuntu onto my USB key from the Ubuntu 7.10 Live CD.  When I set the BIOS to boot from the USB key I get the error "Invalid or damaged bootable partition".  When I set it to load off the computer hard drive t loads GRUB and when I select the Linux partition it loads off the USB key.  

I'm going to be getting rid of GRUB pretty soon but I still want to load Ubuntu directly off the USB key.  Any advise?

---

### Post by dcstar on 2008-01-09
> **icanrule said:**
> I just installed Ubuntu onto my USB key from the Ubuntu 7.10 Live CD.  When I set the BIOS to boot from the USB key I get the error "Invalid or damaged bootable partition".  When I set it to load off the computer hard drive t loads GRUB and when I select the Linux partition it loads off the USB key.  

I'm going to be getting rid of GRUB pretty soon but I still want to load Ubuntu directly off the USB key.  Any advise?

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by ramasan on 2008-01-21
total n00b here.

i have a 8GB corsair USB key.  7.10 gutsy livecd.

i have followed the following directions, which after reading the wiki, seem pretty much to be the same thing.  of course there is probably a slight difference here and there, which of course is all it takes to make a difference, but to my untrained eye i think its the same thing.

i followed this[ pendrivelinux.com article]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") to install:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

i tried three seperate times.  the first i typed the commands.  the second time i copy/pasted to a terminal window.  the third time i tried the lilo command at the end.

in all cases, when i boot to the key, i get:
Boot error

if i look at the key in disk administrator in win xp, it seems like the partitions are there.

it seems like i am just not partitioning or copying boot files properly?

any suggestions?

---

