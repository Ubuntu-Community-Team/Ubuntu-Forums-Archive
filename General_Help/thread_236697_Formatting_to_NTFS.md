---
title: "Formatting to NTFS?"
date: 2006-08-15
forum: General Help
---

### Post by Breaks on 2006-08-15
I'm just wondering, I have an internal IDE HDD (with no OS installed onto it within a machine that has another HDD with Ubuntu on it) that I need to format to NTFS before I RMA mail it back to the manufacturer, is it possible to format to NTFS from either within Ubuntu itself or outside of it (before the OS boots up) with some form of floppy disk or live CD application / command?

---

### Post by Lunar_Lamp on 2006-08-15
I beleive so yes.  Firstly you need to make sure the drive is unmounted.  Then go to system>administration>gnome partition editor, select your hard drive and partition and format it to ntfs using the options in there.  Should be pretty straight-forward.  Remember that you will lose all the data on any partitions that you format.

---

### Post by Tomosaur on 2006-08-15
I don't think any linux tool actually has the capability to format TO NTFS, although I may be wrong. We can't even get writing to NTFS working properly :/

---

### Post by aeiah on 2006-08-15
borrow / steal / use a windows cd, perhaps? if you have an xp cd you could install it via vmware for the task. its pretty easy to do, there's a good howto on the forum. or download windows vista beta for free and use that.

DOS >6.2 should do it too, aparently. im not sure if any free boot cds will because ntfs is proprietary

---

### Post by Ramses de Norre on 2006-08-15
When it's not possible through GParted I think the easiest way is putting it in a windows machine (from a friend or whatever) and partition it through windows.

---

