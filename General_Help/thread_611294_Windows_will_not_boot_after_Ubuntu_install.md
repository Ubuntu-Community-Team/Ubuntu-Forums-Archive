---
title: "Windows will not boot after Ubuntu install"
date: 2007-11-12
forum: General Help
---

### Post by mustafu on 2007-11-12
Hello everyone,

I've recently installed Ubuntu alongside my Windows XP.  The installer resized the existing NTFS partition, then partitioned what was necessary for the installation.  Installation was very smooth, however, when I select the "Windows" option in the boot loader, it just seems to "stall" and won't continue.  Normally, not being able to boot into Windows isn't such a big deal, but I wasn't quite done with it yet =)

I'm not sure where to begin with this.  The Windows partition itself is whole and the data is still intact.  Any help offered would be greatly appreciated, thanks in advance!

---

### Post by meierfra on 2007-11-12
Could be just a grub problem (but I'm not sure).
 post the output of

sudo fdisk -l 

and

cat /boot/grub/menu.lst

---

### Post by weblordpepe on 2007-11-12
Windows doesn't like critical hardware changing. Especially the disk. It may be that anti-piracy thing that it does when you change motherboards.

---

### Post by mustafu on 2007-11-12
Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e8df454

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2701    21687750    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2702        3649     7614810    f  W95 Ext'd (LBA)
/dev/sda5            2702        2786      682731   82  Linux swap / Solaris
/dev/sda6            2787        3649     6932016   83  Linux

/boot/grub/menu.lst:

title Windows
    rootnoverify (hd0,5)
    chainloader (hd0,0)+1

---

### Post by meierfra on 2007-11-12
menu.lst looks fine. So I think it's a windows and not a grub problem. 

I would recommend  getting Super Grub and try to fix the Windows boot sectors. 
See [Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") for information on Super  Grub.

Anyway, Windows isn't my area of expertise. So anybody who has any other suggestion, please jump right in.

---

### Post by mustafu on 2007-11-13
Hello,

Thanks again for the responses.  I then proceeded to try the SUPER GRUB Disk with no luck.  I wonder if it may be a possibility that the NTLDR and ntdetect.com files are corrupt somehow.  Sure, it would be easy enough to just reinstall or run a repair, but I was hoping to find out what happened for future reference.  Is there anything else I could look into?

---

