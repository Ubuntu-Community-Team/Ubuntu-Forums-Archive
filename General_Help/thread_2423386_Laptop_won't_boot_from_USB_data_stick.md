---
title: "Laptop won't boot from USB data stick"
date: 2019-07-22
forum: General Help
---

### Post by desconocido on 2019-07-22
I am running a Toshiba Satellite laptop on which I have installed Ubuntu Mate 16.04.

I downloaded ubuntu-mate-18.04.1-desktop-amd64.iso
from [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)

On my Ubuntu Mate 16.04 laptop I ran
System -> Administration -> Startup Disk Creator
I used the .iso file as source and 
a new 16GB USB "pen drive" or "data stick" as "Disk to use".

The stick now contains 687 items, totalling 2.0 GB.

I leave the stick in an USB3 slot.

I closed down the laptop and rebooted, pressing also the F2 key.
I get the BIOS options page, I go to "Boot" and change the order so that USB comes before the Hard Disk.
"Save and Exit", the computer resumes booting and boots from the hard disk.

I closed down the laptop and rebooted, pressing also the F12 key.
I get the "Boot Menu".
"USB" is item number 1. I press "Enter", the computer resumes booting and boots from the hard disk.

Am I doing something wrong?

---

### Post by desconocido on 2019-07-22
More information:
```
$ sudo fdisk -l

Disk /dev/sdb: 14.8 GiB, 15846080512 bytes, 30949376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4ad90688

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 3920639 3920640  1.9G  0 Empty
/dev/sdb2       3841944 3846615    4672  2.3M ef EFI (FAT-12/16/32)
```

---

### Post by desconocido on 2019-07-22
Putting the USB drive into an USB 2.0 slot and/or removing the USB mouse while booting makes it work.

---

