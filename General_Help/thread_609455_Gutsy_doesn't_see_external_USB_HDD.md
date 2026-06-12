---
title: "Gutsy doesn't see external USB HDD"
date: 2007-11-11
forum: General Help
---

### Post by ramjet_1953 on 2007-11-11
Just discovered an interesting issue regarding an external USB HDD.

I was running Gutsy initially on a spare 60Gb HDD to try it out before committing to the upgrade from Feisty.

I then used CloneZilla to copy the Gutsy disk image to my 120Gb drive which previously had Feisty installed on it.

The copy went fine and I then expanded my /home partition to fill the drive.

I then installed the drive and all is a source of joy, until I try to mount the original 60Gb drive, which is now housed in a USB enclosure. The system does not even see it.

I then tried reversing the drives by putting the old 60Gb back into my laptop and the 120Gb into the USB enclosure - same problem.

What is weird, is that I have another 80Gb HDD with Windows and Dapper on it and when I put this into the USB enclosure my system sees it and mounts it!

All other things like cameras, USB sticks, printers, external DVD writers mount perfectly.

Any ideas?????

Regards,
Roger :confused:

---

### Post by anubhavrocks on 2007-11-11
After you connect the USB HDD post the output of 
```

dmesg
lsusb -v

```

---

### Post by ramjet_1953 on 2007-11-11
Thanks for your reply.

I'm beginning to wonder if it has anything to do with the security of Gutsy being upgraded?

her's the output of lsusb:

> roger@roger-laptop:~$ lsusb
Bus 005 Device 004: ID 04cf:8818 Myson Century, Inc. Fast 3.5" External Storage
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 03f0:3b11 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
roger@roger-laptop:~$ 

As you can see, the external USB device is seen.

I'm wondering also if maybe I need to look at fstab settings?

Regards,
Roger :cool:

---

### Post by anubhavrocks on 2007-11-12
Also check whether the filesystem is detected correctly,the output of dmesg can help you in that.

---

