---
title: "Trouble mounting vfat partition after installing ubuntu from kubuntu"
date: 2006-08-01
forum: General Help
---

### Post by atomic007 on 2006-08-01
Here's the situation I'm in.  I appreciate any help anyone can provide.  I searched online with no luck, and I hope this isn't much of a noob question.  

I have two drives in my system.  A serial ATA '/dev/sda' and regular IDE '/dev/hda'

I used to have kubuntu installed where everything was mounted from / on /dev/sda.

The /dev/hda was a vfat partition used for data backup.  I created the vfat partition using cfdisk.  Everything worked great.  Also forgot to mention kubuntu by default put the bootloader on /dev/hda, I had no choice in the installer I would have preferred sda1.  

So, I backed up my /home/~ directory on hda1 and proceeded to install regular ubuntu ( no kde ).  The install went fine and I placed it on the sda drive same as before.  However now I have a big problem.  No matter what I do I can't mount the hda drive to retrieve my data.  I tried this:

[B]sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
[/B]
and got this:
[B]
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

**fdisk -l** provides this:

[B]Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4982    40017883+   c  W95 FAT32 (LBA)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             638       14593   112101570   83  Linux
/dev/sda2               1         637     5116671   82  Linux swap / Solaris

Partition table entries are not in disk order[/B]

So I think the drive partition may stay be intact.  My guess is the installer for ubuntu corrupted the vfat partition in some way when installing the bootloader on that drive perhaps when I installed ubuntu.  

Does anyone have any ideas on how to recover that lost partition?  and my ever so needed /home/~ backup?

Thanks in advance...

---

