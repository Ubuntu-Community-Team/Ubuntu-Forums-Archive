---
title: "Double boot"
date: 2013-02-03
forum: General Help
---

### Post by zoldik on 2013-02-03
Hello everyone,
At first, I was an microsoft fun user, and curious about linux world, so I had install Ubuntu 12.10 for evaluation, in partition no exceeding 43 Gb. :(

After using ubuntu more than one month, I want to use it always, and to be a new Linux user.  "Open your mind, use open source"  :p
I want to keep win7 for friends, and exceptional uses.

this is the output of "fdisk -l" of my hard disk.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x195c195c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   206852939   103426438+   7  HPFS/NTFS/exFAT
/dev/sda2       206853001  1465147391   629147195+   f  W95 Ext'd (LBA)
/dev/sda5       206853003   795586994   294366996    7  HPFS/NTFS/exFAT
/dev/sda6       795587063  1111360634   157886786    7  HPFS/NTFS/exFAT
/dev/sda7      1111360702  1366826264   127732781+   7  HPFS/NTFS/exFAT
/dev/sda8      1453150208  1465147391     5998592   82  Linux swap / Solaris
/dev/sda9      1366827008  1453144063    43158528   83  Linux

Partition table entries are not in disk order
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
I want to know if it's possible to reverse the windows partition (/dev/sda1) 107 Gb, to linux partition (/dev/sda9) 43 Gb, and vise versa. Without lost my configurations in both systems.

Thank you all,:)

---

### Post by Impavidus on 2013-02-03
As far as I know, Windows isn't happy on a logical partition and the current linux partition, /dev/sda9, is a logical partition. And win7 is space hungry, so 43GB for a system partition is tight (but probably possible). Exchanging the linux and windows partitions doesn't sound like a good idea to me.

I noticed you have several big NTFS partitions, probably containing just data (/dev/sda{5,6,7}). Maybe you can shrink those and let the linux partition grow into that space. It's easiest when moving the swap partition to the end of the disk. People say swap partitions can best be placed at the end of a disk anyway.

And have fun using Linux. I completely stopped using anything else about five years ago.

---

### Post by Mopar1973Man on 2013-02-03
I agree. Windows is a very space hungry every time your turn around the WinSxS folder is growing and no way to prune it back. So I would leave it alone personally if you use windows more so. Personally myself I do mostly everything out of Linux now and rarely I mean rarely ever fire up Windows except maybe for a game that WINE or Virtual Box won't run. So in my configuration this is what I've done...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230987&stc=1&d=1359932783[/IMG]

---

### Post by Mark Phelps on 2013-02-03
You should probably "shrink" the Win7 OS partition and "grow" the Linux partition -- and move all the partitions in-between to the left.

To shrink Win7, do NOT use Gparted, but instead, use the Win7 Disk Management utility.  Using GParted risks corrupting the Win7 filesystem and rendering unbootable.

Once you do that, you will have unallocated space between the Win7 partition and the Extended partition.  You should next use GParted and expand the Extended partition to the left to take up the unallocated space.

After that, you would want to move each partition to the left, until you reach the Linux partition, which you should then expand.

But, since Gparted can't work on mounted partitions, you would need to boot from an Ubuntu LiveCD or Live USB and run Gparted from that.

---

