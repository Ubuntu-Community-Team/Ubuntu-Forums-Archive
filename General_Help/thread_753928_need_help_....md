---
title: "need help ..."
date: 2008-04-13
forum: General Help
---

### Post by oranxess on 2008-04-13
hey there ...  i will tell you my prploem ...
i have installed Ubuntu in a USB ( 2 GB ) .... after  that i restarted the computer and an error came up : 
GRUB error 15
and the other time : 
GRUB 21
i cant access to my other OS ( windows ) because of this error ...
 i haven't installed Ubuntu yet ... only from the live CD ...

---

### Post by hurtstotalktoyou on 2008-04-13
> **oranxess said:**
> need help ...

We would be glad to try and help, but in the future please use a  more descriptive thread title.

> hey there ...  i will tell you my prploem ...
i have installed Ubuntu in a USB ( 2 GB ) .... after  that i restarted the computer and an error came up : 
GRUB error 15
and the other time : 
GRUB 21
i cant access to my other OS ( windows ) because of this error ...
 i haven't installed Ubuntu yet ... only from the live CD ...

It sounds like whatever you did installed or tried to install grub to your hard disk, which is now going bonkers, perhaps because ubuntu is on a usb device.  I would recommend downloading the bootable gparted cd, and checking to see if your disk has been repartitioned.  If so, restoring the partitions should do the trick.  Then you can use your xp disc to "fixboot" if you're still having problems.

If that doesn't work, there are other options, but that's probably you're best bet.

---

