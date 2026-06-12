---
title: "Too many primary partitions in windows dual boot"
date: 2013-05-18
forum: General Help
---

### Post by buckey206 on 2013-05-18
hello all,

I have a dual boot setup with Windows 7 and Ubuntu 13.04 (i made the /home on a seperate partition for ease of updating) which came back to bite me in the butt because now i cannot make a shared media partition.. 
My hard drive looks like this,

Windows boot-100mb
Windows       -100GB
Root (/)        -10 GB

extended
linux swap    -10GB
/home          -85GB

and 726.5 unallocated



i would like to make all of the leftover 726.5 a shared partition for media. 

how would i go about doing this, much appreciated.
thank you,
Jared B.

---

### Post by oldfred on 2013-05-18
You have used all 4 primary partitions, but can have an unlimited number of logical partitions as long as they are inside the extended partition.

So expand extended partition to include all of the unallocated and then create a new NTFS shared data logical partition in the extended.

You have to use Ubuntu liveCD or a gparted livecd as you cannot work with mounted partitions. And liveCD often mounts swap so you may have to click on swap and right click swap off.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6 Has NTFS template to use.

Edit:
Your 10GB while functional is not generous. If you will be using Ubuntu a lot I might make it larger maybe 20GB before you add a lot of data to a data partition and make it more difficult to reorganize.

---

