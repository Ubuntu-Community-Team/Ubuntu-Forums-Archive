---
title: "dualboot question help please"
date: 2012-11-09
forum: General Help
---

### Post by YZCO on 2012-11-09
Here's the deal on a 500 gb hard disk i want to make a 100 gb ext 4 linux partition a 100 gb ntfs windows partition and a third partition to store files in. So here is the question what type of partition do i need to make on the 300gb remaining space so that both windows and linux can read it? I thought another ntfs partition would be ok because i know ubuntu can read ntfs filesystem. And another thing.. would storing the extra files like movies and music in a seperate filesystem on the same hard disk slow things down or overheat or make the battery die faster?? thank you in advance :)

---

### Post by Erik1984 on 2012-11-09
NTFS is the best format for that shared partition. I basically have the partitioning scheme you describe and it works great. For me it doesn't (noticeably) slow things down to have most personal data on a NTFS partition.

---

### Post by oldfred on 2012-11-09
NTFS is good as long as you have Windows to occasionally run chkdsk. 
Ubuntu cannot run filechecks on Windows formats, but normally runs fsck on every 40 or 60 reboots of Ubuntu on Linux formats.

If all your data is in a shared data partition you do not even need 100GB for Ubuntu. I normally install in 25GB for / but have data in both NTFS and ext3 partitions. I have my Firefox & Thunderbird profiles and all photos for the Windows version of Picasa in my NTFS. Then it is the same bookmarks, email & photos in all my installs.

Storage on drive does not really make any difference. CPU, display & Video make all the difference on power consumption.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

You will need to mount partition(s) with fstab.
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by YZCO on 2012-11-10
wow thanks guys that was very helpfull=D> i guess the only problem i could have right now would be with mounting the filesystems incorrectly but that probably wont be an issue if i use the partition editor in the ubuntu disc and do everything from scratch :P im gonna mark this as solved\\:D/

---

