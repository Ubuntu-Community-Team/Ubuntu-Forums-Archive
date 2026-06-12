---
title: "Partitioning usb drive"
date: 2007-06-15
forum: General Help
---

### Post by vishnumrao on 2007-06-15
I have a 160 Gb PATA HDD, which on which was installed Fiesty. I recently upgraded to a bigger drive. I am trying to use the old drive as a external usb drive. 

When I try to partition it with Gparted, I can see only one partition of 130 Gb while the full size of the disk is 160 Gb.

I tried printing the partition table from fdisk  which is as follows.

Command (m for help): p

Disk /dev/sdf: 137.4 GB, 137438952960 bytes
255 heads, 63 sectors/track, 16709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          13      104391   83  Linux
/dev/sdf2              14       16983   136311525    b  W95 FAT32
/dev/sdf3           16984       19457    19872405   8e  Linux LVM

Command (m for help): 

I tried to delete the partition in fdisk, but when deleted it does not show up as extra unallocated space.

The third /dev/sdf3 is the one which is not being seen from Gparted. I tried hooking up my drive to a friends windows machine, to try and partion through Partition Magic. But Partition Magic, sees the drive, but cannot format it. Any suggestions?

Thanks in advance.
Vishnu Rao.

---

### Post by airblade on 2007-06-15
It's normal that the disk size is a bit smaller than claimed by the manufacturer.
This has presumably nothing to do with Ubuntu.

---

### Post by vishnumrao on 2007-06-15
> **airblade said:**
> It's normal that the disk size is a bit smaller than claimed by the manufacturer.
This has presumably nothing to do with Ubuntu.

Small size is ok with me.  But not about 20 Gb. 

If you notice the stats of the partition:
 
/dev/sdf3 16984 19457 19872405 8e Linux LVM

19872405 / 1024 / 1024 = 18.95 Gb. 

I believe it has something to do with being a Linux LVM type filesystem.

Any other suggestions. Thanks.

---

### Post by hdwrguy on 2007-06-15
Some external cases for hard drives don't support drives larger than ~128G.
If your external case says it supports LBA 48 then this is not your problem.

---

### Post by vishnumrao on 2007-06-15
> **hdwrguy said:**
> Some external cases for hard drives don't support drives larger than ~128G.
If your external case says it supports LBA 48 then this is not your problem.

hrwrguy,

Thanks for your reply. I tried connecting the pata drive as a slave drive on my desktop. Same result. So it is not the external case not supporting more than 128 Gb. 

Moreover, sometime back (almost a year back), I had connected the same hard drive to the same external case and it worked fine. I was able to use all the 1260 Gb of space.

---

### Post by airtonix on 2007-06-15
PATA? is that the horrendous Jmicron controller ? if so i think you mayneed to address a kernel patch.....hopefully not since that was a while ago....

---

### Post by smoker on 2007-06-15
just a few suggestions:

try the 'gparted live-cd', and boot from it, i've always found it far better than the ubuntu one, i've never had a problem with it:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

failing that, if you have a floppy, download a win98 boot disk, and install the drive as your master, boot from the floppy, and fdisk it in dos, then format fat, once done, use the gparted app to re-format in whatever linux file system you require. you can get a win 98 boot disk from here:
[http://www.bootdisk.com/](http://www.bootdisk.com/)

another possiblilty, go to the drive manufacturers web site, and download their own diagnostic to check and format the drive.

best of luck

---

### Post by vishnumrao on 2007-06-15
> **airtonix said:**
> PATA? is that the horrendous Jmicron controller ? if so i think you mayneed to address a kernel patch.....hopefully not since that was a while ago....

PATA: Its the normal IDE drive. Not a controller.

---

### Post by vishnumrao on 2007-06-15
Hello smoker,

I have already tried the Gparted live-cd. Same as the gparted from within Ubuntu. 

Floppy disk: No floppy drive. 

 drive manufacturers diagnostic tool: I will try that.

I am going to try to use the windows XP cd and see if windows installer is able to format the filesystem to NTFS.

thanks for the inputs.  Will update this thread on the outcome.

---

