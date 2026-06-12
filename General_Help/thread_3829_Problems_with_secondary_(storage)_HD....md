---
title: "Problems with secondary (storage) HD..."
date: 2004-11-09
forum: General Help
---

### Post by DyDx on 2004-11-09
This has happened in the last release of Ubuntu as well as this latest, Warty. (I haven't, however, tried any other Linux distros in quite awhile)

I have a 160 gb Seagate HD on /dev/hdb1 that doesn't want to work in Ubuntu. From the very first time it booted up (and every time since) it has had a LONG list of:

Buffer I/O Error on Device hdb1, logical block ##############


Someone at Arstechnica had the same thing happened to him so he just turned-off fsck for vfat filesystems (which I don't know how to do, personally).  Regardless, he was able to mount the drive (I don't know, however, if he was able to mount it before turning of fsck for vfat -- I assume so).  I can't mount it, however:

root@x1-6-00-50-8d-e3-9b-1b:/mnt # mount -t vfat /dev/hdb1 /mnt/storage
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       or too many mounted file systems

If I run cfdisk /dev/hdb I get the error:

"FATAL ERROR: Bad primary partition 0: Partition ends after end-of-disk, Press any key to exist cfdisk"

If I run regular fdisk and verify the partition, it says:
Total allocated sectors 312592708 greater than the maximum 312576705

and if I print the partition table it shows:

Command (m for help): p

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19458   156296353+   7  HPFS/NTFS


HOWEVER, this hd works perfectly in Windows XP, and I defragged it last night for good measure.

What could be going on here?  Is there some way to "fix" this drive without formatting? Maybe a tool like Partition Magic could do the trick?

Help! This has all my "valuable" data!

Thanks!

---

### Post by DyDx on 2004-11-09
Damn! I just realized my stupid mistake -- the partition is in fact NTFS :( (why, oh why, did I format it as NTFS??)

It'd still be nice to know how to get rid of the buffer i/o errors, however!

---

### Post by zugzug on 2004-11-13
I'm affraid I have the same problem, and since no solution has been posted I'm having a try here again.
I just installed Ubuntu (working fine all the way), however the startup is real slow. Just after the message "starting RAID devices", which my motherboard, an Asus a7n8x deluxe, supports but I don't use, it just keeps giving messages saying:
> Buffer I/O error on device hdb5, logical block 234451328
This continues about 5 minutes, each time with another block identifier. 

When started however I am able to mount the ntfs-formatted drive and read from it. What is the problem, the RAID or something else? How do I fix this?

The error message:
[img]http://zugzug.eml.cc/DSC00203.JPG[/img]

---

### Post by zugzug on 2004-11-14
Solved it! I simply disabled RAID, after finding out howto do that (sudo dpkg-reconfigure mdadm). Finaly the startuptime becomes more durable...

Now if only I could figure out how I make Ubuntu accept more than 1 sound source without telling me het can't open /dev/dsp...

---

