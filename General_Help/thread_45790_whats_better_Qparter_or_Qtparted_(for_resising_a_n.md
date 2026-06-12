---
title: "whats better Qparter or Qtparted (for resising a ntfs drive partition)"
date: 2005-07-01
forum: General Help
---

### Post by Omnios on 2005-07-01
Quick question what is better for resising a 120G ntfs partition qparted or QTparted. Currently I have my second os (XP) on the fisrt half and want to resise to add about 40 to 50G fat 32 for my documents to share with Linux. I read that some patitioners screw up XP partition tables so that is my main concern. Which is better? Also feeling a bit uneasy about the 0 before and 0 after as it is a bootable drive?

---

### Post by Xian on 2005-07-01
[QUOTE=Omnios]Quick question what is better for resising a 120G ntfs partition qparted or QTparted. [/QUOTE]
Do you mean gparted or qtparted? 

They both use the parted application so I would imagine it makes little difference save that you might prefer one GUI over the other. Personally, I use the Ubuntu installCD for my partitioning. It also uses parted, but I find the other GUI's somewhat confusing and leaves me prone to make some errors. For example, in qtparted the "number" of the partition doesn't always match the partition number (I know that sounds weird), and so I have to remind myself to look at the correct representation. 

I'd also recommend making backups of anything you can't afford to lose, and read the parted [documentation](http://www.gnu.org/software/parted/manual/html_chapter/parted_toc.html).

---

### Post by Omnios on 2005-07-01
Found out that Gparted would not resize my 120G ntfs drive. Used QTparted and worked like a charm. DIdnt use it to make the new partition did that in XP disk management. Now only problem I have is XP wont format fat 32 over a 32G size. I used XP as I heard some fat 32 setups have a problem where Xp can't read the new drive. Now if I can solve the formating part. Was recomended not to mix a disk managment partition with other systems but If I can find a solution that already worked it should be fine.

This thread was ment to see what program was better to use.
This is a Link to my partiton thread. 
[http://ubuntuforums.org/showthread.php?t=45605](http://ubuntuforums.org/showthread.php?t=45605)

---

