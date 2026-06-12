---
title: "Disk space lost"
date: 2015-01-10
forum: General Help
---

### Post by Ralph L on 2015-01-10
If I do Nautilus>Properties>Basic on my USB drive that I use for backup, I find in the third line "65,650 items, totalling 62.9 GB".  However, down below, next to the pie diagram I find 148.0 GB Used.  How do I get back my disk space?  This is a 250GB USB hard drive that I have partitioned into a 37.7GB fat32 partition and a 189.8 ext3 partition.  I brought up nautilus with admin permission, did ctrl-h to show hidden files, and did shift-delete to delete all trash files.  This brought back some space, but not all of it.

Any help appreciated.

---

### Post by mooreted on 2015-01-10
Disk Usage Analyzer might show you what is using up the disk space. It should already be installed.

---

### Post by Ralph L on 2015-01-11
If I take a vote on the different numbers I get apparently the larger one is correct.  This morning (after some disk use) I mounted the USB drive on a xubuntu system that has both Thunar and Nautilus on it.  Thunar said that I had 135GB used and Nautilus said (in the third line of Properties that I had 70GB used, while on the pie chart 155GB used.  When I issued "df" under Terminal I got 142GB used.  I don't know how to account for the differences among the 135GB, the 155GB, and the 142GB, but apparently the 70GB is plainly incorrect. Disk Usage Analyzer says that I have 145GB in use.

My conclusion is that everybody counts differently, but that Nautilus plainly has a problem.  That's disconcerting, because as far as I know Nautilus with Eiciel is the only file manager that supports Access Control Lists, which I use.

---

### Post by Holger_Gehrke on 2015-01-11
The biggest number might include the blocks reserved for root , 5% of total size by default. This can be changed using tune2fs.

---

