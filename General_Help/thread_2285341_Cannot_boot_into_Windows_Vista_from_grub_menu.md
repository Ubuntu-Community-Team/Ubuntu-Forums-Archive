---
title: "Cannot boot into Windows Vista from grub menu"
date: 2015-07-04
forum: General Help
---

### Post by Gadre_Nayan on 2015-07-04
[COLOR=#111111][FONT=Ubuntu]I had installed Ubuntu 14.04 on Already installed Windows Vista on the same partition /dev/sda.

 I have the older BIOS based laptop NOT UEFI.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I was able to work on both Ubuntu and Windows selecting either one from the grub menu. Due to some power problems suddenly my Vista is unable to boot. I tried safe mode, but even that hangs at some CRC.sys entry and does not proceed. [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I even tried a Windows option (previous working configuration) but that hangs as well. I suspect some corruption in the windows boot section.
[/FONT][/COLOR]
I can access the C: drive of Windows from Ubuntu. 
/media/gadre/88F8788CF87879F0 -> This is my C drive.

[COLOR=#111111][FONT=Ubuntu]However I am not aware of the steps/commands to correct this issue. Please help on this. If possible any solution that DOES NOT involve complete installation would be much appreciated.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
My fdisk -l command shows:[/FONT][/COLOR]

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc0ae53aa

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    98710278    49354115+   7  HPFS/NTFS/exFAT
/dev/sda2       171552768   312575999    70511616    7  HPFS/NTFS/exFAT
/dev/sda3        98711550   171552767    36420609    5  Extended
/dev/sda5        98711552   167378943    34333696   83  Linux
/dev/sda6       167380992   171552767     2085888   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by cariboo on 2015-07-05
Moved to General Help.

---

### Post by yancek on 2015-07-05
It would be helpful if you could post the exact error message you get when you select vista.  The Ubuntu Grub bootloader does not directly boot windows but chainloads, basically pointing to the area on the partition where the boot code should be.  Generally, you will need a windows disk to repair this.  There are a number of possible methods to repair at the link below and it might be possible using boot repair which is explained at this link.

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

