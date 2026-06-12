---
title: "2nd hard disk &quot;mirroring&quot; first on boot"
date: 2007-06-22
forum: General Help
---

### Post by newway on 2007-06-22
I have installed Ubuntu7.04 on my desktop with 2 250G SATA disks.
Originally I wanted to use Raid-1 but struggled a long time in vain. 
So finally I gave up and just install ubuntu to the first hard drive (sda)

however the second hard drive (sdb) experiences weird behavior. I can format it and mount it
without any problem, but once I reboot the machine, the second hard drive is being "mirrored"
to the first hard drive(sda). i.e. sda currently used 240G, with only 10G free space left, and gparted shows that sdb used up 240G.

try to mount sdb gives complain:
 wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error

If I re-format it  I can mount and use sdb as normal.

so I am suspecting sth in the boot sequence loaded something about raid control. Anybody has
a clue? I just want to use my second hard drive , no more raid.

---

### Post by nocturn on 2007-06-22
> **newway said:**
> I have installed Ubuntu7.04 on my desktop with 2 250G SATA disks.
Originally I wanted to use Raid-1 but struggled a long time in vain. 
So finally I gave up and just install ubuntu to the first hard drive (sda)

however the second hard drive (sdb) experiences weird behavior. I can format it and mount it
without any problem, but once I reboot the machine, the second hard drive is being "mirrored"
to the first hard drive(sda). i.e. sda currently used 240G, with only 10G free space left, and gparted shows that sdb used up 240G.

try to mount sdb gives complain:
 wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error

If I re-format it  I can mount and use sdb as normal.

so I am suspecting sth in the boot sequence loaded something about raid control. Anybody has
a clue? I just want to use my second hard drive , no more raid.

look in /proc/mdstat to see if it is part of a raid array.

If it is, remove it with mdadm --remove and partition it again (not only formatting).

---

### Post by newway on 2007-06-22
thank you for your quick reply,
there is no mdstat file inside /proc...

---

