---
title: "2TB Partition Woes....and grub/gpt"
date: 2006-12-09
forum: General Help
---

### Post by hytek on 2006-12-09
Well, need some help to figure this out.

I have 2 servers that were custom built with 16x500 gig drives in a Raid5. This gives me a usable storage area of round 7TB. I ultimately wanted to create 40G to /, 4G swap, 4TB and a 3TB ext3 partition. Since it is a hardware raid I did not want to put any part of the Linux install on a separate disk, including /boot.

Now, a piece of info. I would be content with multiple 2TB partitions.

The first time installing with amd64 6.06 and msdos partitions went pretty good. Up until the point I was to create my 2TB partitions. With a max of 4 primary, and the extended being beyond 2TB, gparted, parted, and fdisk just did not want to work with me with the extra large extended partition. :(

Second time installing was with gpt partitions. This would be fine as it would allow me to work with 4TB partitions, only problem is that grub will not load on a gpt partition. There is a program, gptsync, that will sync the mbr and gpt, but it is 32bit only, so again, back to square one. :(

On my third time, and is basically at the same point as #1. Stuck with an extended partition that is way to large and will not work. :(

My last option is to install a small sata drive for /boot as msdos, and then use gpt on the raid. I am hoping this will work and ultimately get me my 4TB and 3TB partitions.

Anyways, is there any hope for me on getting the msdos type extended partition to work with my 7TB space so I can create a few 2TB logicals? or will a separate sata drive be the answer I'm looking for and get my large partitions?

And last question, if I need to reinstall again with a small sata for /boot, what command can I use to convert (or destroy) the msdos so I can convert it to gpt and vice versa? (I have been breaking and recreating the raid to get rid of the msdos/gpt and that takes about 2.5 hours ](*,) )

---

### Post by hytek on 2006-12-09
Ok, well looks like I am going to have to try a separate sata drive for /boot.

So, anyone know a command to use to destroy the mbr, or convert from msdos to gpt?

I really don't want to destroy the raid again ](*,)

---

### Post by perimere on 2007-12-13
It's not quite the same, but I have a smaller setup than you.

I'm running 64-bit Feisty on a dual boot 40GB SATA (XP on the other partition), and a Highpoint 6 Disk RAID 5 for 2.3TB on a GPT partition. This works fine for me.

I don't have the exact steps handy that I followed but I found that like you, most tools don't work above 2TB. From memory I found a walk through online and I thought it was using parted.

I'll have a scout around and see if I can find some more info.

I'm about to add another disk to my array, so I'm looking for info on extending my partitions/ext3 filesys up once the capacity has been added ....

---

### Post by hytek on 2007-12-13
1. With the current version of grub, the boot partition needs to be on a msdos partitioned hard drive (grub cannot boot off of a gpt type partition)
2. Setup the raid with the remaining drives and format using the gpt partition type (may need to destroy the master boot record of the drive with dd to change it to gpt)

dd if=/dev/zero of=/dev/sda bs=512 count=1


3. use parted to create the partitions on the new drive.

[LIST=1]
[*]parted (to start parted and create partitions)
[*]mkpart (command to issue to create partitions)
[*]ext3 (the file system type)
[*]sda1 (the partition name)
[*]1GB (the starting block or size location)
[*]4000GB (the ending block or size location) (can use the command "print free" to get the ending number)
[*]quit (to exit parted)
[/LIST]


4. format the new partition with ext3
[LIST=1]
[*]mk2efs -j /dev/sda1
[/LIST]


5. Add the new partition mount in /etc/fstab


This will get you above and beyond the 2TB limit ;)

Cheers

---

### Post by fjgaude on 2007-12-13
As an aside, the default file size for ext3 is 8 GBytes. There is a command, but memory slips, to change that higher. The default is 4K block size which equates to the 8 GB. I believe ext3 can go to 64K block sizes.

---

### Post by psusi on 2007-12-13
As of gutsy, grub understands gpt partitions.  Which version were you trying this with?

---

### Post by hytek on 2007-12-13
6.10 was the last time I had to build over a 2TB partition server, and grub was not able to boot off of a gpt partition.

I will be having a need again in 2 months for another multi-TB server, so I will be trying 7.xx+.

Thanks for the update.

Cheers.

---

### Post by fjgaude on 2007-12-13
> **psusi said:**
> As of gutsy, grub understands gpt partitions.  Which version were you trying this with?

Gosh, this is news... I guess I missed hearing of that capability. Thanks for the heads up.

---

### Post by pgjensen on 2007-12-26
i do the parted steps to create a partition and then mkfs.ext3 on it... works fine until i reboot and then the system only recognizes it as 800gb instead of 5tb.

any ideas?

---

### Post by psusi on 2007-12-26
You're going to have to be more specific about what you see.  What does parted show the partition table looks like?  What does df show?

---

### Post by Yfrwlf on 2008-03-06
Parted should show the real size of your disk if you do a "p".  If it shows the right size, you should be able to use it to create a partition with the same size (put in -1s for END argument for last sector) or you can use gparted to create the partition.  If it doesn't show the right size then you're probably using MSDOS label format I would think.  Be sure to mount it, copy files to it, and reboot and test it because after I did that all the files were corrupted for some reason.  YMMV

---

