---
title: "[SOLVED] Grub not booting sdb"
date: 2007-12-23
forum: General Help
---

### Post by Zavior on 2007-12-23
I feel I bit stupid because I have done this before with out trouble but now it is killing me!
So here's the deal. I have Ubuntu installed on an 80GB IDE drive. I have Windows installed on an 80GB SATA drive with two partitions (each has a copy of XP on it so I have two Windows XP OS's). Right now I can boot Ubuntu or Windows by changing the HDD boot priority in my BIOS. So I know my SATA drive has a good XP bootloader and my IDE has a good GRUB bootloader. However having to change the HDD boot order all the time is very annoying. So I went to add my Windows drive to GRUB. No go, it gives me an error when I try to boot Windows from GRUB. I have tried the following using (sdb1) and then (hd1,0).

```
title		Windows XP Bootloader
root		(hd1,0)
makeactive
chainloader	+1
```

I am positive that it should be sdb1 but that does not work for some reason. Here is the output of sudo fdisk -l

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1ada1ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9634    77385073+  83  Linux
/dev/sda2            9635       10011     3028252+   5  Extended
/dev/sda5            9635       10011     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfdebfde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6528    52436128+   7  HPFS/NTFS
/dev/sdb2            6529        9728    25704000    f  W95 Ext'd (LBA)
/dev/sdb5            6529        9728    25703968+   7  HPFS/NTFS
```

I don't understand why it is labeling the first disk (my IDE drive) as a sda. Shouldn't it be hda? I thought that SATA and SCSI drives were labeled sd (serial drive) and IDE's were labeled hd (hard drive).

Any help on how to get GRUB to boot to my Windows drive would be much appreciated! Thanks in advance!

---

### Post by logos34 on 2007-12-23
you need to add [mapping for 'virtual swap]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows")' (to trick XP):

> title		Windows XP Bootloader
root		(hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
makeactive
chainloader	+1

/boot/grub/device.map should look like this:

(hd0) /dev/sda
(hd1) /dev/sdb

Since Feisty release ubuntu uses the libata scsi storage driver for both ide AND sata, hence they all show up as 'sd_' (although my maxtor ide drives still show as hda, hdb, so there are apparently exceptions)

---

### Post by Zavior on 2007-12-23
Thanks! Worked great! I knew it had to be something like that. It really threw me when I found that it was labeling my IDE as a serial drive. Thanks for the explanation and help!

---

### Post by logos34 on 2007-12-23
glad to hear.  enjoy!

---

