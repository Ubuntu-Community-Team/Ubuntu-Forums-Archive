---
title: "storing multimedia on FAT32 or NTFS?"
date: 2007-02-23
forum: General Help
---

### Post by billdotson on 2007-02-23
I have an external 300GB USB harddrive that I have Edgy Eft installed on.  I want to use the remaining space (except for a 20GB NTFS partition for backup) to save music and videos (like recorded TV shows)  

What I am wondering is actually should I just have the entire drive formatted as an extended partition full of 30GB FAT32 partitions (with the exception of the ext3 and swap for Ubuntu)

I know that NTFS isn't writable safely with Linux or anything other than Windows and that NTFS supports compression, active directory and encryption but I don't really need any of those things for multimedia files do I? Or is FAT32 less reliable and more likely to get corrupted?  I should keep my Windows backup stuff on a NTFS partition though right?

---

### Post by frodon on 2007-02-23
The only real disadvantage of FAT32 is that you can't store file larger than 4Go and it can be annoying if you are going to record big videos.

---

### Post by Netsui on 2007-02-23
You might try NTFS-3G. Many people have had success with it and I heard it was pretty stable.

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

The above URL is the homepage for NTFS-3G.

---

