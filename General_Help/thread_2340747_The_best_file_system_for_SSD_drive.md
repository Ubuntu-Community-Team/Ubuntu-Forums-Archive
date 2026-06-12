---
title: "The best file system for SSD drive"
date: 2016-10-21
forum: General Help
---

### Post by van hanegen on 2016-10-21
Hi,
just purchased sams t3 external ssd (250Gb). And my question is: do i need to format it to Ext4, or default exFAT would be a better choice for my Ubuntu 16.04?
Thank you

---

### Post by nothingspecial on 2016-10-21
Depends what you intend doing with it. If it is for Ubuntu only then something like ext4 but if you need might what to plug it into another operating system then you'll want something else.

---

### Post by oldfred on 2016-10-21
If an SSD and not a memory card either use ext4 if only Linux ext4 or NTFS if using Windows.
[https://en.wikipedia.org/wiki/ExFAT](https://en.wikipedia.org/wiki/ExFAT)

But be careful with Windows 8 or later as the fast start up in Windows which is always on hibernation will leave the drive mounted when you shut down. Not sure if using Windows to unmount then frees it, but Linux will not read hibernated file systems.

NTFS may need chkdsk regularly, so only use it if you have access to a Windows system or have created the Windows repair/recovery flash drive, as you cannot run chkdsk from Linux.

---

### Post by van hanegen on 2016-10-21
This is not an issue for me, because i'm not going to use it with any windows install. But what about durability. I mean, if formatting in  the Ext4 cause decreasing of the lifespan of the ssd somehow

---

### Post by nothingspecial on 2016-10-21
Formatting ext3/4 will not decrease the life of the filesystem

---

### Post by van hanegen on 2016-10-22
So, Ex4 is the best choice for me
Many thanks!

---

### Post by HermanAB on 2016-10-22
Don't worry about durability.  It will likely outlast you, since the built in little drive controller will shuffle things around on its own to level the wear.

---

### Post by kpatz on 2016-10-22
ext4 is fine and the recommended choice for a Linux (Ubuntu) install.  Current versions will install a cron job that will "trim" the drive on a regular basis to keep it running at peak.

---

### Post by kurt18947 on 2016-10-22
If you were REALLY concerned about flash wear, I guess you could use EXT2 which is non-journaling so makes fewer writes. It's also not fault tolerant because it's non-journaling as I understand it so something like a power interruption could cause significant issues.

[INDENT=2]**[Ext2]("http://en.wikipedia.org/wiki/Ext2")**  is not a journaling file system, and when introduced was the first to  allow for extended file attributes and 2 terabyte drives. Because Ext2  does not use a journal it has significantly less writes applied to the  disk.
- Due to lower write requirements, and hence lower erases, it is ideal for flash memory especially on USB flash drives.
[/INDENT]
[INDENT=2]- Modern SSDs have a increased life span and additional features that can negate the need for using a non-journaling file systems.
[/INDENT]
[INDENT] 
[http://www.howtogeek.com/howto/33552/htg-explains-which-linux-file-system-should-you-choose/](http://www.howtogeek.com/howto/33552/htg-explains-which-linux-file-system-should-you-choose/)
[/INDENT]

I've used EXT2 on flash drives for the above mentioned reason and it seemed to work okay for data. Cheap flash drives have cheap controllers so I would not expect the sophisticated monitoring and wear leveling of SSDs. I'd also guess that $4.99 flash drives do not have the highest quality most durable flash chips.;)

---

### Post by kpatz on 2016-10-22
If you don't want journaling, it can be turned off in ext4--this is better than using ext2 since ext4 supports TRIM.

```
sudo tune2fs -O ^has_journal /dev/sda1
``` (of course, replace /dev/sda1 with your drive/partition.  Run an fsck afterward).

Or create the filesystem with journaling turned off from the get-go.

```
sudo mkfs.ext4 -O ^has_journal /dev/sda1
```

I'd also add noatime to the mount options in fstab, this reduces writes by not updating file access times.

If you're creating a filesystem on an SD card or other small, cheap flash storage, ext2 is fine.

---

### Post by kurt18947 on 2016-10-22
Good points. I'd forgotten about being able to disable journaling on EXT4. Even if you can, should you?  I wonder if the risk of flash wear is overstated on PCs.  Servers on busy networks or data centers that write all day long? Sure but PCs or home servers? Maybe not worth the risk.

---

### Post by van hanegen on 2016-10-24
As my Samsung t3 SSD is not on the cheaper side (approx. $100 for 250  Gb), i guess it must be OK with the chip controller it has onboard. So, formatting in Ex4 is the right decision.
Many thanks!

---

