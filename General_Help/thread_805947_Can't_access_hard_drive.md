---
title: "Can't access hard drive"
date: 2008-05-24
forum: General Help
---

### Post by jstorry on 2008-05-24
So, here's what happened. 

I am dual booting XP and Ubuntu 8.04. I wanted to resize my NTFS partition to make more room for Ubuntu. So, I booted knoppix and used qtparted to resize my NTFS partition, leaving about 100 Gigs of free space.

Qtparted, apparently, does not resize ext3 partitions, but I found a thread saying that it would resize ext2 partitions. So I ran tune2fs to convert my ext3 partition to ext2, but much to my chagrine, qtparted would still not resize my partition.

At this point, I had found another thread detailing a 'safe' way to resize your ext2 and ext3 partitions. So, following this, I used fdisk to delete my ext2 partition, and then wrote overtop of it with a new larger partition, same starting block, new ending block. Everything looked OK, so I wrote the changes to disk.

Now, I have no access whatsoever to my Linux partition, Knoppix does not recognize it, nor does fdisk, or fsck.

Here is the output of fdisk:
root@Knoppix:/ramdisk/home/knoppix# fdisk -l /dev/sda

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ff20ff1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15368   123436495    7  HPFS/NTFS
/dev/sda2           15368       38636   186907143+  83  Linux
/dev/sda3           38637       38913     2225002+   5  Extended
/dev/sda5           38637       38913     2224971   82  Linux swap / Solaris

================================================================

and if I run fsck on my Linux partition: 
root@Knoppix:/ramdisk/home/knoppix# fsck /dev/sda2
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

==============================================================

The suggested command ( e2fsck -b 8193 <device> ) returns:
root@Knoppix:/ramdisk/home/knoppix# e2fsck -b 8193 /dev/sda2
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sda2
Filesystem mounted or opened exclusively by another program?

=============================================================

Any direction would be appreciated, I don't know what I've done, but it would be nice if I could at least get my data off of there.

Thanks,
Jesse

---

### Post by jstorry on 2008-05-24
Alright, nvm, using TestDisk I was able to restore my previous configuration.

Now, I just have to figure out how I can resize my ext3 partition.

---

### Post by lud666 on 2008-05-24
I'm no expert, but I always use the Gparted live cd to change partitions, and have never had any problems. You can get it [HERE]("http://gparted.sourceforge.net/livecd.php").  Gparted might also be included in the Ubuntu live cd, but I'm not sure.

---

