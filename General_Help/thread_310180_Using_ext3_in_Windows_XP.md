---
title: "Using ext3 in Windows XP"
date: 2006-11-30
forum: General Help
---

### Post by sugna on 2006-11-30
I'm about to install Ubuntu as a dual boot with my existing installation of Windows XP.  Ubuntu will be installed on its own hard disk, separate from Windows.  However, all the data that I want to share between Ubuntu/WinXP is also on my windows disk (in a separate partition to the Windows system and program files), which is formatted with NTFS.  So all that data will have to be put into a partition with a mutually compatible file system.

I understand that FAT32 is usually used as the shared file system.  However, I have recently learned about the [ext2 Installable File System for Windows]("http://www.fs-driver.org/") (ext2IFS), which allows Windows to see and work with ext2 and ext3 volumes.  Since ext3 offers a few advantages over FAT32, at least from the Linux end, I am considering using ext3 as my shared file system, with ext2IFS enabling Windows to see it.

Am I asking for trouble?  Is this a sensible thing to do?  Or am I likely to regret it when some unexpected problem emerges down the track?  I'd especially like to hear from someone who has extensively used ext2IFS and can vouch for its reliability or for the sensibility of this approach.

I should stress that my existing windows installation (system files, program files, settings, etc) will remain safe on its own NTFS partition.

Assuming that this is a sensible way to go, is there an easy way to convert a partition from NTFS to ext3 without wiping the data and reformatting it?  It's not such a big deal since I'll be backing everything up anyway, but I'd be interested to know all the same.

Thanks!

---

### Post by scrook on 2006-11-30
I've been using the Windows EXT2/3 driver for a few months. Though admittedly I haven't spent much time actually using Windows, I haven't had any problems. Every application i've tried has no problems opening/saving files on the EXT partition.

---

### Post by aysiu on 2006-12-01
> **scrook said:**
> I've been using the Windows EXT2/3 driver for a few months. Though admittedly I haven't spent much time actually using Windows, I haven't had any problems. Every application i've tried has no problems opening/saving files on the EXT partition.
Same experience as scrook's: I hardly ever boot into Windows, but when I have used [http://www.fs-driver.org](http://www.fs-driver.org), it's worked just fine.

---

### Post by Adramelech on 2006-12-01
Actually i had some problems, but maybe was cause of my ignorance, when trying to copy certain files to NTFS from ext2, the driver failed, I think was cause permissions, but not sure if ext2 on windows check for that.

---

### Post by RAOF on 2006-12-01
> **sugna said:**
> ...
Assuming that this is a sensible way to go, is there an easy way to convert a partition from NTFS to ext3 without wiping the data and reformatting it?  It's not such a big deal since I'll be backing everything up anyway, but I'd be interested to know all the same.


Sadly, no.  You'll have to reformat.

---

