---
title: "Error msg:  No object for d bus interface"
date: 2017-04-18
forum: General Help
---

### Post by pat4 on 2017-04-18
Hi,
I have a desktop computer running Ubuntu 16.04, 64 bit.  Four hard drives are installed - one for OS and three for backup / file storage. 

I have a problem when mounting one of the drives in Nautilus. I get the message "Unable to mount Disk 3 - no object for D-Bus Interface"

I have tried a couple of things suggested in this and other forums....  

1. using GParted to a allocate a new UUID  

and  

2. unmounting and removing gvfs, then rebooting


I had mixed results.  Using solution 1, I find I can then mount the drive for the rest of my session, however if I reboot I have to allocate another UUID before I can mount the drive again.   Using solution 2 made no difference at all. I was unable to mount the drive after reboot.    The other drives mount without problem through Nautilus - it is only this one drive that gives me the error. 

Anyone help with a permanent solution or point me in the direction of where the problem may lie please?

Many thanks.    Pat.

---

### Post by ian-weisser on 2017-04-18
What can you tell us about the drive that's hard to mount? Filesystem? SMART test results? Size?

---

### Post by pat4 on 2017-04-19
The disc is a Western Digital, type WDC WD1002FAEX-00Y9A0.
 1TB.
7.9% full
Currently running at  a cool 23 deg C.
File system is Ext4  (as are the other discs).
Write cache is enabled

Having run SMART tests there are no errors to report or areas of concern. 

Thanks...

---

