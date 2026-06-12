---
title: "Best media drive file system"
date: 2007-01-27
forum: General Help
---

### Post by travs.cd on 2007-01-27
I'm planning on installing Ubuntu on my desktop machine, but i need write capabilities for my media drive. Currently the file system is NTFS, but all my files are backed up and I'm ready to format with a different file system if needed.

I'm planning on using Ubuntu for my main OS, dual-booting with XP for games.

the data that is stored on this drive consists of mp3s, movies, etc.

I am aware you can add NTFS Write support in Linux (not too comfortable with this though) and that you can also add Ext2/Ext3 Read/Write support in XP.

or would FAT32 be 'ok'? :neutral: 

(it should also be noted that this drive is 320GB)

---

### Post by chalex on 2007-01-27
If you want to be able to access the drive read/write from multiple OSes (Win, Linux, OS X) format it FAT32.  Problem solved.

---

### Post by taurus on 2007-01-27
I would make that share partition as ext3 instead of fat32 since ext3 is much better and that ancient filesystem--fat32.

And as you have already known, you can read and write to ext3 with [http://www.fs-driver.org](http://www.fs-driver.org) from XP.

---

### Post by GrammatonCleric on 2007-01-27
Are you attempting to migrate to Ubuntu or is this just a test to see if Linux is for you?  

If you are keeping your media files under 4gig FAT32 will work.

If some of your movies are 4gig+ or if you are migrating to linux I would go the route of EXT3 and install the ext2fs driver under windows from either...

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

or 

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)


Personally, I would avoid going the route of getting linux to read and write NTFS under linux unless you REALLY have to.  It's sort of a pain especially so if FAT32 or EXT3 will work for you.

-GC

---

