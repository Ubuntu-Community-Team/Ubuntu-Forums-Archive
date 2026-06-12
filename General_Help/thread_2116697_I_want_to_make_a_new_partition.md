---
title: "I want to make a new partition"
date: 2013-02-16
forum: General Help
---

### Post by sinaphysics on 2013-02-16
Hello dears,
I have two directory, one is "/ " and the other is "/home". I want to make new partition on home folder and separate 20 gig of it for installing Fedora. Just care I have some files on "/home" which I use them in ubuntu. So installing Fedora should be alongside ubuntu. Do u have any suggestion ?

---

### Post by carl4926 on 2013-02-16
Can we suggest you take a screenshot of your HD partitions in Gparted and post it here

---

### Post by Mark Phelps on 2013-02-16
You're mixing terms -- which can be confusing.  

A partition is a physical chunk of space -- a fixed size segment of a hard drive -- which can then contain multiple folders and files.  

A folder is a logical thing and does not have a fixed size -- since its size is the total of all the files contained inside it, plus a little overhead.

Partitions contain folders, not the other way around.

Also, "/" and "/home" are likely to be folders, not partitions.

We need to see how your disk is organized before providing detailed advice.

---

### Post by sinaphysics on 2013-02-16
Sorry I had some problem with Gparted. I've posted about it before but it wasn't solved. I use ubuntu disks to make a photo. I think this is almost satisfying.
this is [link]("http://i.imgur.com/oJEOETc.png").

---

### Post by pbrane on 2013-02-16
Using gparted on a live CD/USB drive you should be able to resize the partition of your choice. You must make sure the partition to be resized is not mounted, that's why I say to use gparted from a live CD or USB media.

It's not clear to me from your screenshot which partition has what directories on it, but it looks like partition 6 is the one to resize. That should be /dev/sda6 in gparted. I assume that is the one mounted at /home? It looks like you may have partition 1 mounted at /.

---

### Post by carl4926 on 2013-02-16
Almost certainly the OP is wanting to shrink sda6

I use PartedMagic's Gparted

You should shrink from the far right to the left and don't shrink too much. I recommend, no more than half of the free space
So if you say have 50GB free, only take 25GB.

Backup important data before you do any of this.

---

### Post by sinaphysics on 2013-02-16
Ok. This ideas are great. But I want to know resizing by gparted(live usb) doesn't affect my files( I want too keep them ). And in continuous is it possible to have same "/home" folder for Fedora and Ubuntu ? 
You guess true I want to shrink Partition 6. and my root(for ubuntu) is partition 1.

---

### Post by sinaphysics on 2013-02-16
How to delete unwanted post. I post the previous one mistakenly for two times.

---

### Post by oldfred on 2013-02-16
We do not delete things unless spam. 

You cannot share /home. Too much chance of overlap of different settings.

You may be able to share data, And it think Fedora was changing to use 1000 which Ubuntu uses for the first user.
       Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)
    
Fedora likes to use LVM and have a separate /boot outside the LVM. Some have posted it may be better to just install in ext4 partition. 
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by pbrane on 2013-02-16
As oldfred has stated you don't want to share your /home directory. Many issues there; especially with different distros.

As for your question about resizing and keeping your directories/files, I have resized partitions several times without having any issues. gparted will move data to resize partitions. However as carl4926 has pointed out you should **backup all data** before making any partition changes. There is always the chance that something will go wrong.

---

### Post by sinaphysics on 2013-02-16
Ok, dear friends. Now imagine I want to replace ubuntu with Fedora totally. I want to make partition1 as root folder " / " and partition6 as home folder "/home". You think it would be OK to delete whole "~/.Folders" in home directory which involve Ubuntu and just keep my own media files ?
I find this useful for partition scheme. 
[http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s2-diskpartrecommend-x86.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s2-diskpartrecommend-x86.html)

---

### Post by carl4926 on 2013-02-17
> **sinaphysics said:**
> Ok, dear friends. Now imagine I want to replace ubuntu with Fedora totally. I want to make partition1 as root folder " / " and partition6 as home folder "/home". You think it would be OK to delete whole "~/.Folders" in home directory which involve Ubuntu and just keep my own media files ?
I find this useful for partition scheme. 
[http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s2-diskpartrecommend-x86.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/Installation_Guide/s2-diskpartrecommend-x86.html)

You could keep /home. But with Fedora use a different username.
Once installed, work on copying your files and possibly changing the ownership.
I'd still backup

If you are not familiar with the new Fedora - it's installer and partitioner might confuse you some...

---

