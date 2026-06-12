---
title: "Help with partitions and files"
date: 2006-11-08
forum: General Help
---

### Post by theone1_ on 2006-11-08
Hi, I have a 16gb HDD on a FAT32 file system. It is running Windows 2000 currently but I'd like to install Ubuntu. I'm making room for it all as I'm typing this, but am slightly confused about file systems in relation to Linux based OS.

So, what I would like:
1 Partition holding Win2k - already on the system. This would be the secondary OS.
2 Partition for Ubuntu, big enough for all programs and installations needed. Is 3GB or so enough?
3 Partition to hold ONLY files - ie. music, images, documents, etc. able to be accessed by both OS.

Is this relatively easy job to do?

Thank you

---

### Post by Kateikyoushi on 2006-11-08
Fat32 is accesible from linux if you create an ext partition for linux you can access that from both OS as well. Here is the windows ext driver. [LINK]("http://www.fs-driver.org/")

I can't tell the exact minimum size required by the default install but I wouldn't make a partition smaller than 5 GB for / and a 512MB swap.
If you do a custom install can live with less.

Resizing the partitions is quite straightforward but do a backup of your important data just in case and defragment the drive.
Following this installation guide might also help. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by theone1_ on 2006-11-08
> **Kateikyoushi said:**
> Fat32 is accesible from linux if you create an ext partition for linux you can access that from both OS as well. Here is the windows ext driver. [LINK]("http://www.fs-driver.org/")
Sorry, could you detail this?
So, Fat32 is able to be read and written by both OS, so I just make a partition ext3 for Linux?
Is this Windows ext driver just so I can see the Linux partition in Explorer?

Thanks for your reply

---

### Post by Kateikyoushi on 2006-11-08
Yes, fat32 could be read and writtend from windows and linux therefore creating one more partition which both OS can write is unnecessary.
Ext3 is the the default filesystem type ubuntu uses, with the ext driver you can read and write ext partitions as they were fat or ntfs check the screenshots.

If you partition manually you need at least two partition for linux a / and a swap.

---

### Post by indytim on 2006-11-08
You might want to consider adding another HD.  16GB for both Windows 2K and Ubuntu - Gnome and/or KDE is getting pretty tight.

Just a thought.

IndyTim

---

### Post by theone1_ on 2006-11-08
The reason I wish to have Windows is just for compatibility. I don't game, so I don't require much space or processing power. I have a Pentium 550 with 256mb ram on this machine.

I opened GParted, and an error saying that it is unable to read the contents of the filesystem.. any solutions to this? I ran a chkdsk through Windows, and no problems were found.

---

### Post by theone1_ on 2006-11-08
Also, when I run the Live CD in normal Graphics mode , it loads all the stuff before, but when going into the desktop it goes nuts and has a black screen with writing, litterally, all over the place.

My graphics card is an NVIDIA RIVA TNT/TNT2 Pro 16mb

---

### Post by DagonSphere on 2006-11-08
theone1_

Let's say you create an ext2/3 partition that both OS's can read.  You cannot share that ext2/3 partition ("drive" in Windows terms) across the network when booted into Windows.  This is mentioned the the troubleshooting area for the ext driver.  I'd read that area as well as the faqs before making a final decision.  If you have one PC, then just ignore this.

Though I couldn't find it in either area, I seem to remember there being a problem where the EXT driver would only be able to access the first partition of a physical HDD.  It may have been a different EXT2/3 driver, so don't quote me on that.

And yeah, I recommend another drive as well.  But for Ubuntu, I think the minimum install is under 3 gigs.  Add 512 MB for swap, and add at least a few gigs for growing space.  It's easy to add another drive later and move things around.

As far as the graphics card issue goes, did you try booting the live CD into "Safe Graphics Mode"?  It's the second option when you get to the 30 second delay when booting off the CD.  It's strange, but I have that same graphics card, and have no problems with it.

HTH :)

---

