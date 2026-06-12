---
title: "Best clone drive with compression?"
date: 2019-02-20
forum: General Help
---

### Post by ProDigit on 2019-02-20
I'd like to know, if there's a program that can clone partitions and drives to USB flash stick, with compression; copying only active clusters (not deleted files or clusters).
Meaning, if I have a 100GB drive, with 8GB used, it should fit on an 8GB USB stick, or smaller depending on the compression ratio.

Possibly make the flash stick bootable too; and all under Linux?

In the Windows 98 era, there was Norton utilities. But I haven't found something similar for Linux....

---

### Post by TheFu on 2019-02-21
It depends on the file system being used by the source.  If ext3/4, then fsarchiver, partimage, clonezilla all do the compression of actively used sectors ... but they don't make bootable disks.  Please check the manpages for each of those tools, since the file system support does change. Without the file system support, they do compressed images and do get all the bits.  You can make that better by filling up the empty parts of the disk with a zero filled file, then remove that file. Compression for the images will be great.

fsarchiver is the only tool of this sort that will let you restore to a smaller partition, to my knowledge.

But if you seek an efficient backup tool, doing image-based backups isn't very efficient.  Something like duplicity, which is file-based, not image-based, would be a better choice if doing backups daily or weekly.

---

### Post by ProDigit on 2019-02-22
My system is working almost perfect now.
I just want to back it up, before I make an error and mess it up again, and have to reinstall everything.
It took me 2 hours to set everything up just the way I wanted it, and I've become a pro at getting things done quickly manually.
But I'd rather have a faster way to restore my drive.

I could possibly just rar the entire drive to a thumb drive, and copy it back to the harddrive, provided the boot (UEFI) and partitions are still working fine.
This will be most case scenario.
My Linux often gets messed up, when trying to follow some advice online about fixing something, and I end up breaking it instead; due to outdated, or simply incorrect advice.


Anther way was to create an ISO file of my drive,
Transfer it to USB,
plug that USB in a Windows computer,
and use a Windows ISO program that can compress the ISO, 
Then use Rufus to create a bootable disc from a DSL type of Linux (a small, bootable Linux), or perhaps even the live CD Linux, to boot from and perform dd to write the ISO to the HDD/SSD.
The problem I'm having with Lubuntu, is that it takes only 4GB of space, but even if I have an 8+GB drive, the remaining space is locked.
I can't add any additional files to the live USB.

---

### Post by TheFu on 2019-02-22
If all this sounds like too much effort and you have a desktop, then the easy answer is probably just to use **aptik** for your desktop backup tool.  Be certain to test what it does with a restore. Putting that test into a virtual machine is the easy way that doesn't risk harming anything.

If you want read-write storage on a flash drive, then you'll likely need to have multiple partitions. I don't actually know, because I don't use flash drives to run OSes that store data. Much too slow.  I do boot from ISOs on flash drives all the time - btw, tinycore is 16mb if you need a tiny system for online banking.  But for pretty much anything else, I just use the Ubuntu Mate or Ubuntu Server ISO to boot and do what I need.  This is a common way to fix broken Linux systems.

---

