---
title: "Help with Gparted, dual booting windows 7 and Ubuntu"
date: 2013-07-18
forum: General Help
---

### Post by coreyjohnson711 on 2013-07-18
Hey there, I am trying to add unallocated space to the extended parition where Ubuntu currently resides. Right now there is a small system reserved partition, windows 7 partition and then Ubuntu on the extended partition. I shrunk the size of the Windows partition sda2, and would like to add that unallocated space to my Ubuntu partition. See attached screenshot. Is this possible?

Got a little further, but now get an error message, see here:
Can't have overlapping partitions

Tried allinging with cylinder instead of Mib and it magically worked

---

### Post by oldfred on 2013-07-19
Drives have not used cylinders since hard drives became large than 8GB about 15 years ago. Is your BIOS still set to IDE? If so may be better to set to AHCI but you may need to install drivers into Windows 7 first.

I would just use the space as /home. To move it around will take a lot of time and moving data always has a risk. If you want to move data make sure you have good backups as any power failure leaves drive half moved and then it is corrupted. You have to move extended partition left to include the unallocated, Then move sda5 left, then expand sda5 right. Do each task separately do not queue them up.

Better just use space as /home. YOu can move extended partition left to include unallocated so unallocated is inside the extended. Then new partition will be a logical.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Or you can just make it a data partition.
      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

