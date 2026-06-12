---
title: "250gig HD, Which filesystem should I use?"
date: 2007-02-20
forum: General Help
---

### Post by C-A on 2007-02-20
I am about to complete my migration from windows. My last step is formatting my hard drive that I use for media (mostly .avi and .mp3). It is 250 gigs. It is currently formatted as FAT32 because  I have used it from both Linux and windows.

I am wondering what type of filesystem to use. From what I have read, ReiserFS seems to be the best choice but I wanted to get some feedback before proceeding. 

If there is anyway to convert from fat32 to ReiserFS  or ext3 without data loss (which I have heard that there is not) I would love to do that because otherwise I will be juggling 250gigs worth of my most valuable files between smaller spare hard drives, dvd's, and some old zip drives.

---

### Post by moshuptrail on 2007-02-20
Just to clarify, what you have is a 250G, single partition, data only (media) HD.  Correct?
Windows and Ubuntu are on some other drive?

---

### Post by C-A on 2007-02-20
> **moshuptrail said:**
> Just to clarify, what you have is a 250G, single partition, data only (media) HD.  Correct?
Windows and Ubuntu are on some other drive?

Yes..Ubuntu is on a separate hard drive.

---

### Post by moshuptrail on 2007-02-20
If I remember, the advantage of ReiserFS is the ability to store extremely large files.  That might be appropriate for your avi and other media files.  Otherwise, ext3 would be fine.
As to how to convert, if there are utilities to convert a fs in place, I'm not aware, but if the drive is less than 50% full you could shrink the partition, create a second partition, then copy from 1 to 2, then convert the first one.

Just an idea...

---

### Post by C-A on 2007-02-20
> **moshuptrail said:**
> If I remember, the advantage of ReiserFS is the ability to store extremely large files.  That might be appropriate for your avi and other media files.  Otherwise, ext3 would be fine.
As to how to convert, if there are utilities to convert a fs in place, I'm not aware, but if the drive is less than 50% full you could shrink the partition, create a second partition, then copy from 1 to 2, then convert the first one.

Just an idea...

Thanks for the reply. The drive is about full but your idea about shrinking the partition will work once I get it down to half which will make the move more doable.

---

### Post by dcstar on 2007-02-20
Have a read of this:

[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

---

