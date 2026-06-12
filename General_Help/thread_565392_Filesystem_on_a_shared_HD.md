---
title: "Filesystem on a shared HD?"
date: 2007-10-02
forum: General Help
---

### Post by cd-r80 on 2007-10-02
What filesystem on a shared external HD? Ubuntu & XP to share. NTFS or EXT3? Now I use two partitions FAT & EXT. I want to leave FAT to history.

---

### Post by overkillm on 2007-10-02
My suggestion would be to get one of those third-party apps that will let Windows read EXT2/EXT3 and use EXT3.

Here is one: [http://www.fs-driver.org/]("http://www.fs-driver.org/").  

I say this mainly because EXT3 doesn't require defragging and I believe it handles file permissions better.  You definitely don't want FAT because of the file size limit. I found this out the hard way, before I discovered ntfs-3g.

---

### Post by cd-r80 on 2007-10-02
Do I use ext2 or ext3? Is there problems writing ext3?

---

### Post by overkillm on 2007-10-04
No problems that I know of.  You can use ext2 if you prefer, I think the only difference is that ext3 has [journaling.]("http://en.wikipedia.org/wiki/Journaling_file_system")
The two are backward- and forward-compatible.

---

