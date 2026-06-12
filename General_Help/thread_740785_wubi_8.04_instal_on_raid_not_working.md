---
title: "wubi 8.04 instal on raid not working"
date: 2008-03-31
forum: General Help
---

### Post by gedbcause on 2008-03-31
I have an 80 gig hdd which contains my XP system and 2 160 gig drives set up as a striped set with 4 partitions formatted ntfs with sata raid. Each of the partitions on the raid set up are about 80 gig each and are identified as K,L,M,and N. I downloaded Ubuntu from the WUbi site onto the completely empty M partition. Upon starting my computer I am asked to select which OS to boot to and when I choose Ubuntu things seem to go ok until what looks like the terminal command line. I have tried all 4 of the boot menues and come up with a lot of errors that amount to a lot of "Not found" under the casper/log command. It seems as if the boot directory which is in C drive does not manage to access the rest of the OS which of course is in the M drive. Any thoughts any one?:lolflag:

---

### Post by ago on 2008-03-31
Wubi/Ubuntu do not support fakeraid. Please try to install it on a "real" partition

---

### Post by gedbcause on 2008-03-31
I'll give it a try. Thanks.

---

### Post by gedbcause on 2008-03-31
PS Should I partition in FAT 32

---

### Post by ago on 2008-03-31
ntfs

---

### Post by gedbcause on 2008-03-31
Thanks a lot! I am posting this reply via Firefox on the now running Ubuntu OS.

---

