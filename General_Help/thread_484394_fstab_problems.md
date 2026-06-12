---
title: "fstab problems"
date: 2007-06-25
forum: General Help
---

### Post by kevmartin on 2007-06-25
AFter recently changing my disk partition sizes (successfully) using GParted, I have a problem.

Linux now seems to think my fstab is no longer correct.  In windows this was reflected in just some shuffling of drive letters around, which is not too much of a hassle.  But in Linux I am stumped as to how to fix the problem.  It certainly seems to be related to fstab (Linux told me so with an error message).

Can anyone point me to resources to help me edit the fstab configuration - I looked at the file and it is not exactly user friendly, written in strange codes and full of comments that it was edited by the upgrade to Edgy (I have since then upgraded to Feisty with no problem - it was only the partitioning with GParted that caused the issue).

Thanks

---

### Post by haricharan on 2007-06-25
can you post your fstab 
```
cat /etc/fstab
```

---

### Post by merlinus on 2007-06-25
Probably the UUIDs got changed with re-sizing the partitions, so

```

sudo fdisk -l

```

and

```

blkid

```

will indicate the needed edits to /etc/fstab.

-merlin

---

### Post by kevmartin on 2007-06-29
What a fool I can be - I forgot to subscribe to my own thread so didnt think anyone had responded 

My apologies - I will do as you suggest and post again (soon as I get a chance to get out of Windows and into Ubuntu for a bit)

Thanks for responding.

---

### Post by kevmartin on 2007-07-01
Having checked the suggested commands I'm still pretty much lost what to do here, so I'll post the results and hope for further instruction :-)

Thanks

cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7 -- converted during upgrade to edgy
UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D6-010B /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/sda2 -- converted during upgrade to edgy
UUID=1CF82850F8282B0A /media/sda2 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda5 -- converted during upgrade to edgy
UUID=191B-4887 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/sda6 -- converted during upgrade to edgy
UUID=a2bc5abb-b7b6-4418-b2f8-c481766fc81e none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

```

fdisk -l:
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       10205    81923467+   7  HPFS/NTFS
/dev/sda3           29788       30393     4867695   db  CP/M / CTOS / ...
/dev/sda4           10206       29787   157292415    f  W95 Ext'd (LBA)
/dev/sda5           10206       22672   100141146    b  W95 FAT32
/dev/sda6           22673       22736      514048+  82  Linux swap / Solaris
/dev/sda7           22737       29787    56637126   83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 82.3 GB, 82348278272 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       10011    80413326    b  W95 FAT32

Disk /dev/sdg: 132 MB, 132251648 bytes
8 heads, 32 sectors/track, 1009 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        1009      129136    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 7, 32) logical=(1008, 7, 32)

```

blkid:
```
/dev/sda6: UUID="f8f812a3-452f-4b05-846b-7412df576e36" TYPE="swap" 
/dev/evms/sda7: UUID="e02c22a8-12fc-458a-b18d-b16bf2fddc97" SEC_TYPE="ext2" TYPE="ext3" 
/dev/evms/sda6: TYPE="swap" UUID="a2bc5abb-b7b6-4418-b2f8-c481766fc81e" 
/dev/evms/sda5: LABEL="DATA" UUID="191B-4887" TYPE="vfat" 
/dev/evms/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/evms/sda2: TYPE="ntfs" 
/dev/evms/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-010B" TYPE="vfat" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-010B" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="191B-4887" TYPE="vfat" 
/dev/sda7: UUID="e02c22a8-12fc-458a-b18d-b16bf2fddc97" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdf1: LABEL="IOMEGA_HDD" UUID="639C-7807" TYPE="vfat" 
/dev/sdg1: SEC_TYPE="msdos" UUID="3CEB-AD4C" TYPE="vfat" 
/dev/evms/sdg1: LABEL="IOMEGA_HDD" UUID="639C-7807" TYPE="vfat" 
/dev/evms/sdf1: SEC_TYPE="msdos" UUID="3CEB-AD4C" TYPE="vfat" 
/dev/mapper/sdg1: SEC_TYPE="msdos" UUID="3CEB-AD4C" TYPE="vfat" 
/dev/mapper/sda6: TYPE="swap" UUID="f8f812a3-452f-4b05-846b-7412df576e36" 
/dev/mapper/sda5: UUID="191B-4887" TYPE="vfat" 
/dev/mapper/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/mapper/sda2: TYPE="ntfs" 
/dev/mapper/sdf1: LABEL="IOMEGA_HDD" UUID="639C-7807" TYPE="vfat" 

```

---

### Post by logos34 on 2007-07-01
well, your UUID (/ root) as output by blkid matches fstab...Can you post one more file, 
**/boot/grub/menu.lst**

---

### Post by twosox on 2007-07-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/107798](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/107798) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I seem to be having a similar problem -- I've just added a new SATA hard drive to my system, and  I can't seem to keep it mapped in the right place.  Every time I reboot, sda and sdc are switched:

```
fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       38913   312560640   83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5133    41230791   83  Linux
/dev/sdc2            5134        5354     1775182+   5  Extended
/dev/sdc4            5355       14593    74212267+  83  Linux
/dev/sdc5            5134        5354     1775151   82  Linux swap / Solaris

```

When I restarted my machine, /dev/sdc1 was listed as /dev/sda1, etc.  So I know something is fishy.



I know for certain that my boot disk is actually an IDE drive -- it's listed in /boot/grub/device.map:

```
(hd0)	/dev/hda
(hd1)	/dev/sda

```
 I actually submitted a bug about this at one point, because when I first installed Feisty, my grub menu and device map were all messed up, and I think it was because it originally saw my IDE drive as a SATA device. ([https://bugs.launchpad.net/ubuntu/+source/grub/+bug/107798](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/107798))

```
blkid
/dev/sda1: UUID="fe2ce7ed-3981-44d0-99e1-36864bccf675" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="64a5d71f-3087-462c-bdf4-86232a990efa" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: UUID="de4f5eb2-72d0-4d10-ac47-eec0aeb74fad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="02c4f2db-5d46-4154-b442-22e70efd52e2" TYPE="swap" 
/dev/sdb1: UUID="eab53cbf-1c9f-449d-b397-9e27ecd7c3e6" SEC_TYPE="ext2" TYPE="ext3" 

```

I downloaded and can run pysdm, which was of some help, and I even tried a gparted livecd to see if that would allow me to assign the drives correctly.  The gparted cd worked pretty well, but when I rebooted my machine, I still get this switching between sda and sdc.

I've been looking on this forum for help, but this looks like the closest thread to my problem.

Thanks...

---

### Post by kevmartin on 2007-07-02
> **logos34 said:**
> well, your UUID (/ root) as output by blkid matches fstab...Can you post one more file, 
**/boot/grub/menu.lst**

Sure, here it is:

```
title           Ubuntu, kernel 2.6.20-16-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-386
savedefault

title           Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro single
initrd          /boot/initrd.img-2.6.20-16-386

title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
savedefault

title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro single
initrd          /boot/initrd.img-2.6.17-11-386

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro single
initrd          /boot/initrd.img-2.6.15-28-386

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 ro single
initrd          /boot/initrd.img-2.6.15-26-386

title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

---

### Post by kevmartin on 2007-07-05
I don't know if it was related, but it did seem to start at the same time as this problem ... Linux was not able to keep time anymore - I would reset the clock and it would start losing time immediately, at a rate something like 1-2 minutes every 10-15 minutes.  Yesterday after doing a Repair on thw Windows installation on another partition of the computer, Linux is now able to keep time again.  No idea what the connection is or if there is one, but I thought I'd mention it anyway.

Thanks - still hoping to avoid a reinstall here.

---

### Post by kevmartin on 2007-07-10
Humbly beg your forgiveness for bumping this in the hope of some help from someone more knowledgable :)

---

### Post by bodhi.zazen on 2007-07-10
> **kevmartin said:**
> Humbly beg your forgiveness for bumping this in the hope of some help from someone more knowledgable :)

Change fstab to this :> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7 -- converted during upgrade to edgy
UUID=e02c22a8-12fc-458a-b18d-b16bf2fddc97 / ext3 defaults,errors=remount-ro 0 1

# /dev/sda1 -- converted during upgrade to edgy
UUID=07D6-010B /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 0

# /dev/sda2 -- converted during upgrade to edgy
/dev/sda2 /media/sda2 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0

/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       0

# /dev/sda5 -- converted during upgrade to edgy
UUID=191B-4887 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 0

# /dev/sda6 -- converted during upgrade to edgy
UUID=f8f812a3-452f-4b05-846b-7412df576e36 none swap sw 0 0

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

All you need to do is pulg in the information from uuid to fstab ;)

/boot/grub/menu.lst looks fine.

---

### Post by kevmartin on 2007-07-13
Thanks for that - I may be missing something, but that fstab posted looks the same as it already is.  I changed the fstab file to that and rebooted and it made no difference.  

Wish I had a clue about this UUID thing but I don't.  Any other ideas?

Thanks

---

