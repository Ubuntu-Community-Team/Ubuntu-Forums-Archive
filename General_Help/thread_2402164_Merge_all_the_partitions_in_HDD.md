---
title: "Merge all the partitions in HDD"
date: 2018-09-26
forum: General Help
---

### Post by nonetheless on 2018-09-26
I previously installed Ubuntu with LVM partitioning. 

Now I want to merge all the partitions to get the whole space in one single partition while reinstalling. Is there a way to do that ?

I cannot use GParted, possibly because of LVM partitions. Any other way ?

---

### Post by ajgreeny on 2018-09-26
Provided you make sure you have good backups of all your personal data files and any hidden files and folders in your home that you want to keep, I think you can use gparted, but will have to use the **Device -Create Partition Table** menu which should remove all from the disk and allow you to start again.

---

### Post by nonetheless on 2018-09-26
Thanks !! I seem to have work through that this time !!

---

### Post by ajgreeny on 2018-09-27
Great news! 

If that really has worked as you wanted, please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

