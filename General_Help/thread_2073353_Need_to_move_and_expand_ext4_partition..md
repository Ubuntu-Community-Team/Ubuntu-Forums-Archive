---
title: "Need to move and expand ext4 partition."
date: 2012-10-19
forum: General Help
---

### Post by cdmccreary on 2012-10-19
Gateway laptop

Ubuntu 10.10 is reporting that I am out of hd space.  I deleted my windows partitions; with help, I updated grub and am booting again.

|-----------free 116gb------------|----extended 44gb---------|
|---------------------------------|---ext4 33bg---|-swap 7gb-|


1. I need to move the ext4 partition to the beginning of the drive and 
2. to expand it for more space. 

3. Maybe expand the swap partition ...

But for now:  I plan to take ubuntu hard drive out of laptop; put on usb controller; plug into windows machine and use partition software to modify...


Bought windows MinTool Partition Wizard if that will help. 

How do I do it?  (I already mucked it up once!):confused:

---

### Post by oldfred on 2012-10-19
I would use gparted. I have not used the mini-tool but understand it works well for Windows partitions. I often suggest Linux tools for Linux and Windows tools for Windows.

I prefer to not move partitions left, but it usually can be done. The issue is just that any interuption, power failure etc corrupts system. So have good backups before starting. You may have to move extended partition left first if the Linux partitions are in the extended and in gparted click on swap partition and swap off. You must do this from liveCD so partitions are not mounted but liveCD like to mount swap if found to speed things up.

I prefer to split system. Either move /home to where the Windows partition was or make it a data partition and move data from /home into the "new" partition.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)


Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

