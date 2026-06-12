---
title: "Ubuntu XP Vista triple boot problems"
date: 2008-06-12
forum: General Help
---

### Post by blurryone on 2008-06-12
Hi Guys,

I have a HP DV9205TX, it came pre installed with vista ultimate, which i shortly got tired of and started trying out some linux distros on the second hdd. eventually came across ubuntu (now using hardy) and am pretty happy with that.

Then i thought i might as well get rid of vista altogether and go back to XP so i used Gparted live cd to create a new partition on the first hdd so that i could install xp on that and triple boot for a while till i am happy i have migrated everything from vista then destroy the vista partition and go back to xp full time.

However since i created the new partition vista now thinks that it is on drive d: and not drive c: and thus will not load properly.

Is there any way i can change the ntfs drive letters around without changing the physical location of the partitions on the disk? (i want XP to boot off D: but to be on the inside of the table so it is the fastest) but because i created the partition where vista used to be (after moving vista partition to the outside of the table) it thinks its d: not C:...

any idea how i can change this without having to move vista back to the inside? and without having to use recovery mode?

Also my laptop did not come with the vista dvd or anything similar so i can not boot into vista off a disk.

Many thanks guys

Blurry

---

### Post by meierfra. on 2008-06-12
Maybe this helps:

[http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista]("http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista")

---

### Post by blurryone on 2008-06-12
Thanks for that, that is almost exactly the process i went through however where it says put the partition and the END of the drive i did not i put it at the start....

---

### Post by meierfra. on 2008-06-12
So the link did not help?

Open a terminal in ubuntu and  post the output of 


```
sudo fdisk -l
```
(l is a lower case L)

---

