---
title: "USB stick is stuck (pun intended)"
date: 2021-04-03
forum: General Help
---

### Post by transit-y on 2021-04-03
I have a 64GB INTENSO usb stick that I have used only rarely with both Ubuntu and Windows. Since yesterday, when I tried to copy some files to my Windows environment, the operation hung, so I plugged it out (could not stop it properly from the OS) it and plugged it to my Ubuntu 20.04. Ubuntu mounted it and showed the contents, but again I could not copy/delete any files. I started the disk utility and tried to re-format the drive, but this hung too. Again, the only thing that I could do was to plug it out and then back in. Following are some things I tried:


[LIST]
[*]"lsusb" shows
[/LIST]
Bus 002 Device 009: ID 058f:6387 Alcor Micro Corp. Flash Drive

[LIST]
[*]"sudo fdisk -l" shows
[/LIST]
Disk /dev/sda: 59,66 GiB, 64047022080 bytes, 125091840 sectors
Disk model: Speed Line      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf6b335e2

Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1         128 125091839 125091712 59,7G  7 HPFS/NTFS/exFAT
[LIST]
[*]"sudo fdisk /dev/sda" shows
[/LIST]
Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.
<Blinking cursor>

This stays like that for hours and Ctrl-C does not abort the running process - the only thing to do is close the terminal window and plug out the usb stick.

I understand that this may be a hardware problem, but I was wondering if there is something else that I could try to troubleshoot the problem. I don't care about the contents of the usb stick. I would like just to make it usable again, if possible.

Thanks.

---

### Post by ActionParsnip on 2021-04-03
You can use dd to wipe the disk and start again

---

### Post by tea for one on 2021-04-03
> **transit-y said:**
>  I started the disk utility and tried to re-format the drive, but this hung too.

I would see if gparted could create a new partition table - all data on the USB stuck stick will **not** be saved.

gparted > Device > Create Partition Table

---

### Post by C.S.Cameron on 2021-04-03
When my flash drives die, some times they become read only and some times they do nothing.
I think all these multi layer large drives they are making now, just don't have any endurance.

---

