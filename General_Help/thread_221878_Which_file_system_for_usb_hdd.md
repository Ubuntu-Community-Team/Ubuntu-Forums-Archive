---
title: "Which file system for usb hdd?"
date: 2006-07-24
forum: General Help
---

### Post by Lunar_Lamp on 2006-07-24
I want to use a new 250gb USB HDD for storing media, including backups of some of my dvds (i.e. large file sizes).  What file system should I use, as I would like if possible to retain compatilibyt with Windows.

I know ext2/3 can be read in windows, but not natively.
I know NTFS can be read in linux, but not reliably.
I know FAT32 can be read in both, but has a file size limit of about 5gb iirc.

---

### Post by aysiu on 2006-07-24
NTFS can be read in Linux reliably.
It cannot be *written to* from Linux reliably.

Ext3 can be read from Windows but not natively. Still, why does it have to be native. Just install [http://www.fs-driver.org](http://www.fs-driver.org) and you're set.

FAT32's file size limit is 4 GB.

---

### Post by joselin on 2006-07-24
I use EXT3 filesystem for my 250gb usb disk, but i don't need windows compatibility, and i store there very larger files.

Cheers

---

### Post by Lunar_Lamp on 2006-07-24
Sorry, typo, I know that it's writing to NTFS that is problematic.  I would prefer to be able to just plug my usb drive into any windows pc and read it without needing to install software if possible.  As linux is my main OS though, ext3 is my natural choice.

---

### Post by Karma_Police on 2006-07-24
you could try the howto for ntfs 3g driver in this forum: [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+3g)

If you can make it work, it does what you want. plug to windows with no extra software install...

---

### Post by sabredog on 2006-07-24
I split my 40Gb into FAT32 and EXT3 partitions. Best of both worlds then!

---

### Post by Lunar_Lamp on 2006-07-24
just set up ntfs-3g, and all appears to be working well.  though i think my shift key has broken, i have no idea if it is related.  i shall be using ntfs for practicality reasons.

---

### Post by NT4usB on 2006-07-24
I am a recently converted Linux user with a lifetime of stuff (~3TB) stored on external USB drives, all in NTFS.
Plugged one into my 6.06 box, it mounted and read with no problems.
(and, surprisingly, most of them played using the codec's already installed!)

*(Happy Linux user for going on 11 weeks!)*

---

