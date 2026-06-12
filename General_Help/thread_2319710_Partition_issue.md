---
title: "Partition issue"
date: 2016-04-06
forum: General Help
---

### Post by bizres on 2016-04-06
Hello,

I've installed Ubuntu on my 320GB HDD and while all seemed to be working well, suddenly an update failed, saying insufficient disk space.
Surprised, I looked at gparted & disks, to see that the installation has been allocated 255MB and the rest is unallocated free space. Yet I had selected the default partition settings to use the whole disk at time of install.

Not sure what I can do here without messing up the system.

I've attached some screenshots from gparted and disks which I hope can provide some info.

Thanks in anticipation.
[ATTACH=CONFIG]268212[/ATTACH][ATTACH=CONFIG]268213[/ATTACH][ATTACH=CONFIG]268214[/ATTACH]

---

### Post by oldfred on 2016-04-06
You chose the full drive LVM with encryption install option.

Standard disk tools do not work on LVM - logical volumes, nor do they see encrypted partitions.
And many have not been housecleaning the /boot partition which then fills up and runs out of space. I think that issue has been fixed with 16.04 as it now keeps last and new kernel & deletes all others.

I do not know LVM nor encryption:
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html) 

       
 /boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels)
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
Check current kernel I also keep one older just in case:
#Current kernel:
uname -a 

I normally use synaptic to remove older kernels:
      
 Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

