---
title: "Grub Windows 7 (encrypted) entry disappeard"
date: 2013-01-10
forum: General Help
---

### Post by markbeverley on 2013-01-10
Hi there,

I'm running a dual boot laptop with Windows 7 and Ubuntu 12.04. A few weeks ago our IT department rolled out McAffee encryption so I now have a Windows encrypted partition and Ubuntu unencrypted. Everything continued to run as normal until I did an Ubuntu automatic update after which the Windows 7 entry disappeared from Grub. I have tried doing a manual entry in the 40_custom grub file but to no avail. 

This is the output of fdisk -l
```

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x732324dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   156292607    78145280    7  HPFS/NTFS/exFAT
/dev/sda2       156293118   250068991    46887937    5  Extended
/dev/sda5       241965056   250068991     4051968   82  Linux swap / Solaris
/dev/sda6       156293120   241965055    42835968   83  Linux

Partition table entries are not in disk order

```

This is what is currently in my 40_custom file (I've tried various things):
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'Windows XP Professional' {
insmod ntfs
set root='(hd0,1)'
drivemap -s (hd0) ${root}
chainloader +1
}
EOF

```

I have also attached the contents of my grub.cfg file.

Any help would be very much appreciated!!

Thanks,

Mark

---

### Post by markbeverley on 2013-01-11
Just a quick update - I got our IT engineer to decrypt the Windows partition using his McAfee stick and all is now working as it should. I now need to figure out how to encrypt it again without having the same problems. I may try this: [https://community.mcafee.com/message/104053]("https://community.mcafee.com/message/104053")

Mark

---

### Post by Mark Phelps on 2013-01-11
When Win7 first came out, OEMs typically installed it using two partitions on a drive.  The first partition was for the boot files, the second for the OS and apps.  This allowed the second partition to be encrypted.

If you have your Win7 boot loader files in their own partition, they encrypting Win7 should not present a boot problem -- and os_prober will find the boot loader files.

If you have your Win7 boot loader files INSIDE the Win7 OS partition, when you encrypt it, os_prober can't read it anymore and can't create GRUB entries.  Plus, even if you create an entry by hand, it still probably won't work.

---

### Post by markbeverley on 2013-01-12
Hi Mark,

Thanks for the info. Looking a GParted only shows one partition for Windows so I assume the boot loader is on the same partition. However it does say the first sector is 2048 so I'm not sure what's contained from 1-2048? Also that wouldn't explain why booting was still working for several weeks up until I updated Ubuntu.
I will look into repartitioning the Windows drive and moving the boot loader. Interestingly Ubuntu still can't read the Windows partition even though it has been decrypted....

Mark

---

### Post by Mark Phelps on 2013-01-12
> **markbeverley said:**
> ... so I'm not sure what's contained from 1-2048? [...
That's a combination of the MBR and the PBR.

> slso that wouldn't explain why booting was still working for several weeks up until I updated Ubuntu.
No ... it doesn't ... and I don't have an explanation for that.

> I will look into repartitioning the Windows drive and moving the boot loader. 
OK... but don't be tempted to use GParted (in Linux) to do that.  Doing so risks corrupting the Win7 OS partition and leaving it un bootable.

Suggest you download the ISO of the Minitool Partition Wizard Boot CD, burn that to CD, and use that to do the partition changes.

Also, BEFORE you make any changes, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  That gives you the means of repairing the Win7 boot loader -- should anything go wrong.

And finally, download and install EasyBCD in Win7.  That has an option for MOVING your boot loader files from the Win7 partition to another partition -- which is what you will need to do.
> Interestingly Ubuntu still can't read the Windows partition even though it has been decrypted...
OK, then run CHKDSK on the Win7 OS partition.  Ubuntu should be able to read it after that.

---

