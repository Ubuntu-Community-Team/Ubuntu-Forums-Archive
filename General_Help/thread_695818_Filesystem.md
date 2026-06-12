---
title: "Filesystem"
date: 2008-02-13
forum: General Help
---

### Post by thecorleonefamily on 2008-02-13
Hello. I am new to Linux (from Windows Vista).

I have lots of data (movies and Mp3) on a NTFS partition. However, since I am completely going to discard Windows, I need to know what type of filesystem should I use to store this data. 

Should I stick to NTFS only? My novice experience has shown it is problematic considering the write support for NTFS. If not should what filesystem should I use for the " /data "  partition I will make.

---

### Post by kuja on 2008-02-13
I would probably go with EXT3, XFS, or JFS. EXT3 is probably the best all rounder while JFS and XFS both have speed advantages in some areas and fall short in some others. Any of those would probably "do". If it's going to be a paritcularly large partition XFS might be a nice choice seeing as it won't slow your boot time when the partition is checked, especially when compared to most other FSs.

---

### Post by thecorleonefamily on 2008-02-13
Is there any link or something which explains the various filesystems available for Linux?

---

### Post by chrisccoulson on 2008-02-13
You could try here:
[http://en.wikipedia.org/wiki/List_of_file_systems]("http://en.wikipedia.org/wiki/List_of_file_systems")

---

### Post by thecorleonefamily on 2008-02-13
Thanks..

---

### Post by articpenguin on 2008-02-14
if you have movies you might want to choose JFS, JFS does a lot better at large files than ext3.

---

