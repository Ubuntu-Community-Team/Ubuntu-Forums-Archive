---
title: "use a DVD+RW like a floppy disk or hard drive"
date: 2014-03-26
forum: General Help
---

### Post by Spaceman9 on 2014-03-26
How can I format a DVD+RW so I can use it like a floppy disk or hard drive with both Linux and Windows 7? Thanks for any help. I'm using Ubuntu 12.04 long term.

---

### Post by Mark Phelps on 2014-03-26
> How can I format a DVD+RW so I can use it like a floppy disk or hard drive with both Linux and Windows 7? 

As far as I know, you can't.

YEARS ago, there were drivers distributed with CD writers that allowed you to mount the CD as if it were a regular file system.  I know they worked in Windows (but not well), and don't recall seeing them in use in Linux.

Haven't seen those in a long time, so I suspect, they're not around anymore.

While you can ADD to a CD-RW, basically what you're doing is writing a "session" at a time, and simply adding them, one after another.  You still have to "burn" to the drive, though; so it's not really read/write in the sense of a hard drive.

---

### Post by Spaceman9 on 2014-03-26
Thanks Mark,

I was thinking more like UDF or maybe the dd command. I just need to be able to write files and delete files from a DVD+RW just like we do with a hard drive. As far as I know that is not hardware dependent.

---

### Post by TheFu on 2014-03-26
It is hardware dependent.  Not every DVD/CD/BR can do it.  On my DVD-RW, it only worked with specific software provided by the vendor, under Windows. Those disks were not readable by any other system here either, but I didn't pull the optical drive and load the drivers onto any other system to validate. I know the media didn't work in other optical drives - even other DVD-RW drives.

Plus the media was specific too.  After a few tests, I ended up treating that fancy media just like read-only media - it was too hard to keep track of the differences. Perhaps I should re-burn some of it as a test. It has been about 12 yrs, so bitrot has probably set in already. ;(

---

### Post by 3rdalbum on 2014-03-26
You can do this on DVD-RAM discs if your drive supports them. There is no other way to do it.

---

### Post by mc4man on 2014-03-26
You're likely referring to "packet writing". If so then search out that with linux, maybe you'll find something relevant/useful,  maybe not.
(there is an outdated [ How-to]("http://ubuntuforums.org/showthread.php?t=129093") in this forum but it's about 8 years old so pretty much nothing in it can be used verbatim. (or at all..

---

### Post by Spaceman9 on 2014-03-27
Thankx for your help guys. I tried formatting a DVD+RW with the default formatter in Windows 7. It said that would format the DVD so I could use it like a USB pen drive. It didn't work.

I tried formatting a DVD+RW with the Disk Utility in Ubuntu with FAT. Nautilus says the DVD is formatted with FAT 32. I can write files, delete files and move files just as I would with a hard drive  or a pen drive. Windows 7 Though can only see this DVD as a backup disk and will not write, copy nor delete individual files.

---

