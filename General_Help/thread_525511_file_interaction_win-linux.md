---
title: "file interaction win-linux?"
date: 2007-08-14
forum: General Help
---

### Post by nalleballe on 2007-08-14
HI! Im a new xubuntu-user and im dualing with windas$$ untill i get this in the spine. Whats the secret to be able to interact files between these partitions? Whenever im trying to drag a file to the windowspartiton from linux it just goes back. Is it possible to do this and how is it done?

REGARDS NALLEBALLE:popcorn:

---

### Post by loserboy on 2007-08-14
by default ubuntu can read files from windows file systems (NTFS) but can not write to it, and windows by default can not read or write on ubuntu file systems (ext3)

there are some programs that will let you change that... ill post back in a sec when i find the name

---

### Post by loserboy on 2007-08-14
it's called ntfs-3g, if you are running Edgy 6.10 or later it should be in the universe or multiverse repositoreies


what I did instead was make a seperate partition for sharing between xp and ubuntu and I made it Fat32, which both OSes can read/write

---

### Post by az on 2007-08-14
> **loserboy said:**
> windows by default can not read or write on ubuntu file systems (ext3)


In windows, you can install an ext2/ext3 driver at fs-driver.org.  Then linux partitions appear as regular drives in windows (read/write).

---

### Post by ugm6hr on 2007-08-14
This is easy: [http://ubuntuforums.org/showpost.php?p=2687994&postcount=1706](http://ubuntuforums.org/showpost.php?p=2687994&postcount=1706)

This has a good video tutorial link (albeit for Ubuntu - but almost identical): [http://ubuntuforums.org/showpost.php?p=3187933&postcount=1847](http://ubuntuforums.org/showpost.php?p=3187933&postcount=1847)

---

### Post by nalleballe on 2007-08-14
so cool you guys. ill go with both! one part fat and one part ext3-driver. thanx guys! :guitar:

---

### Post by nalleballe on 2007-08-14
even cooler.

---

