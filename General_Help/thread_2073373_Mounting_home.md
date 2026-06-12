---
title: "Mounting /home"
date: 2012-10-19
forum: General Help
---

### Post by lhelber on 2012-10-19
I have 12.04 installed on a SSD.  I now want to move /home onto a large hard drive so the user files are saved on a different partition.  What permissions to I need to set for the new partition so I can mount it at /home.  I tried changing the mount directory from /media/hdd to /home in /etc/fstab but I then couldn't login after I rebooted.

I also want to have /var/www going to the hard drive too.  What is the best type of link to do that?

---

### Post by drmrgd on 2012-10-19
You might have a look at this documentation for how to change the mount point and move these directories to new partitions.  I think this outlines it fairly well:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

While I was trying to dig that link back up from the abyss that is my bookmarks, I also came across this that might be relevent:

[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

---

### Post by oldfred on 2012-10-19
On my SSD I still have /home but all data including some of the large hidden data folders like the Firefox & Thunderbird profiles are on my rotating drives. My /home is about 2GB and the vast majority of that is .wine for Picasa. The user settings are small but as part of system I wanted them on SSD.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Cheesemill on 2012-10-19
Also bear in mind that your home partition has to have a linux filesystem, ie ext2/3/4, xfs, jfs etc.

You can't have your home directory on a FAT or NTFS partition as they don't support the linux permissions system that is required.

---

### Post by lhelber on 2012-10-20
Thanks for your help.  [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) did the trick and I am up and running again.  Sorry I didn't find that document first.

---

