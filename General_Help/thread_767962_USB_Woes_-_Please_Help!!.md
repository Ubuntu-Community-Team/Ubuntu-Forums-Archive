---
title: "USB Woes - Please Help!!"
date: 2008-04-26
forum: General Help
---

### Post by kiwited on 2008-04-26
I have a problem that seems to have begun when I upgraded from 7.04 to 7.1, and which continues into Hardy. My machine no longer recognises some items plugged into the USB ports. Exceptions are the laser printer which is plugged into USB, and the USB mouse. Items which do not work include card readers, USB hard drive and digital cameras.

The same upgrade saw the disappearance of the USB option from Virtual Box, which is also missing with the upgrade to Hardy. I have carried out a fix from the forums involving unchecking four lines from a file - can't remember which one but in Hardy it seems this is done by default. Anyway, it didn't work for me.

Any help would be so appreciated.

System: AMD 64bit 6400+ processor, 2 gig RAM, Radeon HD2600 video.

Theo

---

### Post by kiwited on 2008-04-27
Still hoping someone can shed some light. Also cannot read pen drives or USB hard drive.

Theo

---

### Post by rbmorse on 2008-04-27
What happens when you attach one of the devices that doesn't work and run 
lsusb from a terminal?  Is the device listed? 

Any difference running sudo lsusb?

---

### Post by kiwited on 2008-04-27
Thanks for your reply.
lsusb and sudo lsusb both produced the same result:

theo@Ubuntu:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 002 Device 004: ID 04f9:0028 Brother Industries, Ltd 
Bus 002 Device 001: ID 0000:0000  
theo@Ubuntu:~$ 

The mouse and printer are plugged into the rear usb ports, the other devices I normally use are plugged into the front ports, which have worked in the past. At the time of this test I had a SD card in a built in multi card reader as well as a Kingston Traveller 3 gig pen drive in another usb port.

Thanks,

Theo

---

### Post by rbmorse on 2008-04-27
For testing purposes can you put the pen drive in one of the rear ports and see if it works there?

---

### Post by kiwited on 2008-04-27
I have tried both the pen drive and the USB HDD in the rear ports as well. Neither is recognised.

I have installed the Ubuntu eee 8.04 on my little eeepc and this recognises everything perfectly.

Theo

---

### Post by rbmorse on 2008-04-27
It looks like there might be a problem with UDEV on your computer. 

The best I can recommend at this point is to use synaptic to remove/purge udev and then reinstall it.  You want to purge udev to remove its configuration files. They should be rebuilt when you reinstall the package. You'll have to reboot afterwards.

---

### Post by kiwited on 2008-04-27
Right, purged udev and reinstalled. Rebooted and........oops!

No reboot. After grub there is an immediate error message:

Error 15: File not found
Press any key to continue...

which brings me back to the grub menu again.

Will sort this out first, then worry about the USB again.

Theo

---

