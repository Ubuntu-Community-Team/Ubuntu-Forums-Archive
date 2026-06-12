---
title: "Fregmentation"
date: 2006-08-09
forum: General Help
---

### Post by rekahsoft on 2006-08-09
I have two harddrives with reiserfs partitions on them...i believe reiserfs is a fregmented filesystem...fregmentation can slow down a machine so i was wondering if there are any tools to defregment my drive/s?

---

### Post by Fass on 2006-08-09
There are no specific ReiserFS defragmentation tools. Fragmentation is not supposed to be an issue under Linux, though...

---

### Post by rekahsoft on 2006-08-09
really...that is what i thaught until i ran across something that said that bittorrent fregments it...

---

### Post by The Noble on 2006-08-10
After 30 reboots, Ubuntu autochecks with "fsck", a filesystem checker for fragmentation. The nice thing with linux is that it writes contiguously, so that fragmentaion is not as likely with linux(compared to windows). 

Also, note that linux has several partitions, one of which is swap, which is separate from everything else. Windows is one big block, thus things get messy quick. Don't worry unless you really worry about 2% fragmentation slowing you down.

---

### Post by rekahsoft on 2006-08-10
Yes...windows page file really causes some problems..thanks for the info

---

### Post by yopnono on 2006-08-10
> **rekahsoft said:**
> Yes...windows page file really causes some problems..thanks for the info

Not really. You can disable it, if you have alot of RAM. Or you can set it to a fixed size, or put in on a different partition.

---

### Post by mcduck on 2006-08-10
> **The Noble said:**
> Don't worry unless you really worry about 2% fragmentation slowing you down.If somebody is able to notice the effect of 2% fragmentation, I'm amazed. My music storage drive shows 17,5% fragmentation and works just as fast as my system drive (1.2%)..

Linux filesystems do fragment. But fragmentation doesn't slow them down like FAT or NTFS.

---

### Post by padre999 on 2006-08-10
There is a another thread which discussed the fragmentation issue before. Might be interesting for you to read:

[http://www.ubuntuforums.org/showthread.php?t=203842](http://www.ubuntuforums.org/showthread.php?t=203842)

---

