---
title: "[SOLVED] Ubuntu Gutsy cannot delete"
date: 2008-01-07
forum: General Help
---

### Post by petzworld999 on 2008-01-07
Well, I am trying to delete files off my Windows Partition in order to make room to expand my Linux partition. When I click the 'send to trash' button, it just deletes the files. No disk space is freed. Any help would be appreciated.

---

### Post by Craigus on 2008-01-07
Is the disc space freed if you empty trash ?

---

### Post by petzworld999 on 2008-01-07
There is nothing in the trash to empty. The folder just disappears. I did try to add something from my Linux partition to the trash and it emptied fine, but it did not free any space on my Windows partition.

---

### Post by petzworld999 on 2008-01-07
Wait, never mind. I just found a folder on my Windows partition called '.trash-critta.' That's where all my crap went.

---

### Post by Craigus on 2008-01-07
Ah. This may be relevant:

> COMMON PROBLEM :

* The gnome Trash don't support neither ntfs filesystem nor fat32 filesystem, so when you delete files with nautilus, they don't go in the trash, but in an hidden directory, at the root of the partition, call .Trash-<username>. So to 'empty the trash', you'll have to show hidden files (<Ctrl><H>) and use the suppr function of nautilus on this directory (<Shift><Suppr>

From this thread:

[http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

Edit: beat me to it ...

---

