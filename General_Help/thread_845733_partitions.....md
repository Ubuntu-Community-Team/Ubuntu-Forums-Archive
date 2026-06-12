---
title: "partitions....?"
date: 2008-06-30
forum: General Help
---

### Post by aalr1986 on 2008-06-30
hey people..!!!!

just wanted to know, cause these are the partitions I have in my system:

#1: File System (10gb)
#2: OS (an NTFS partition I have, it's about 100gb)
#3: Family (a 14gb NTFS partition, I have WXP installed there)

so my question is, if I can take some of my free space in other partitions, and assign that space to my Ubuntu partition....

can I do that!??!?

---

### Post by soccerboy on 2008-06-30
> **aalr1986 said:**
> hey people..!!!!

just wanted to know, cause these are the partitions I have in my system:

#1: File System (10gb)
#2: OS (an NTFS partition I have, it's about 100gb)
#3: Family (a 14gb NTFS partition, I have WXP installed there)

so my question is, if I can take some of my free space in other partitions, and assign that space to my Ubuntu partition....

can I do that!??!?

Of course, pop in a live CD with ubuntu, reboot into the CD, and go to System>Administration>Partition Editor.  Then the resizing is very self explanatory.  You have to shrink the partition, then move it and then grow the filesystem.

---

### Post by VMC on 2008-06-30
Here's a great tutorial that will explain in detail what to do and what to look out for, It has pictures to help you. When you re-partition your Windows NTFS you need to have Windows do its autochk first. Instead of copying and paste here just go and read up on it:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

