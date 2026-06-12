---
title: "Best file system for sharing between OSX and Ubuntu?"
date: 2007-07-28
forum: General Help
---

### Post by suterb42 on 2007-07-28
I want to share my backup files between my Mac and my Ubuntu box. Right now, I've got everything on a FAT32 partition, but I was wondering if there was a better file system I could use that would be recognized by both OSX and Ubuntu. I'm seriously thinking about ditching my Windows XP partition, so it doesn't have to be Windows-compliant.

---

### Post by methinks on 2007-07-28
There is a windows driver available which lets windows use ext2 and ext3 (standard linux partitions). I use this to share my drive, it works very well. There's a good chance that you can find something similar for macOS.
My problem with FAT32 is the limit on file sizes (2 or 4 gig max file size, which is a pain when working with video...)

---

### Post by bettlebrox on 2007-07-28
Similar question on Slashdot today that might help you:

[http://ask.slashdot.org/article.pl?sid=07/07/28/1621241&threshold=-1]("http://ask.slashdot.org/article.pl?sid=07/07/28/1621241&threshold=-1")

---

### Post by suterb42 on 2007-07-28
> **bettlebrox said:**
> Similar question on Slashdot today that might help you:

[http://ask.slashdot.org/article.pl?sid=07/07/28/1621241&threshold=-1]("http://ask.slashdot.org/article.pl?sid=07/07/28/1621241&threshold=-1")

I read that, but I couldn't find a decent answer with all that bickering going on. Could someone sum it up for me?

EDIT: Here's the way things are set up:

My Windows/Ubuntu box has a backup hard drive (which will soon become my primary drive once I switch the data over to my other HD). I'm going to be sharing files between the PC and my Mac via SMB. (If there's a better way, let me know.) Should I format my backup drive to NTFS and install MacFUSE on my Mac? If I don't, will I still be able to copy files from my Mac to my PC?

---

### Post by bettlebrox on 2007-07-29
I didn't read it all either because of all the bickering!

If your going to ditch WIndows and go with Mac & Linux, then the HTFS or HTFS+ filesystems would proably be the way to go.

This Gentoo page might help:
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

