---
title: "Help taking space from one partition to another"
date: 2016-12-05
forum: General Help
---

### Post by juntjoo2 on 2016-12-05
So using my apart in a live CD I made an additional partition to house the bulk of my files, then moved my files from my main partition over. Then I shrunk the main partition to make room for my new partition  but I can't seem to access this extra space with this new one. It's like gpart can't reach over to this extra space I've created. Would I have to create a partition first in this empty space, make changes then reboot to have it accessable to my new storage partition or am I missing another step? Thanks!

---

### Post by ajgreeny on 2016-12-05
It would make things a lot clearer to us if you could take a screenshot of the gparted window with that disk chosen in the drop-down box top right.

What filesystem is the new partition formatted to; ext4, or have you just created space and not yet formatted it to a new partition?
It sounds as if you have unallocated space which will never accept any files as it has no filesystem, so in gparted click in this unallocated space and create a new ext4 partition.  For ease of management I suggest you label it **Data** as it will then show in your file manager left hand pane as **Data** and will mount at /media/*username*/Data.

You will need to add it to /etc/fstab to mount it automatically and will need to change the permissions of /media/*username*/Data to allow you to write to it as user. A reboot is not needed, but after editing fstab run command ```
sudo mount -a
```

If you are not sure about how to edit fstab or change those permissions ask again.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by juntjoo2 on 2016-12-06
Thank you. I took a bunch of screen shots but I can move them anywhere due to permissions problems. This seems to happen a lot. Any way to stop this from happening, like to tell my Ubuntu system to stop prohibiting me from doing things in general to my computer? For the stupidest little things like this. Really slowing me down. Anyway, if you have a solution for that that would be great. Otherwise...

Basically, I tried doing the steps one by one, first shrinking my main partition(after taking as many files out of it and putting them into my extra space partition. 

Next I tried creating a new partition with the empty space I created by the shrinking BUT whether I tried to apply this and the first step or apply the first step(shrink) then apply this step I get an error which doesn't explain anything. Just points out I had one or two operations pending that weren't completed.


Anyway, once these operations get completed and I have my original extra space partition and this new one I create from shrinking my main system partition, should I be able to append the little one onto the big one?

---

### Post by oldfred on 2016-12-06
If older BIOS/MBR are you trying to create another primary partition? You have the 4 primary partition limit and can only create logical partitions inside the extended partition.
Post this:
sudo parted -l

If partition is on internal drive, you may want to have it auto mount when you reboot.
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

And the steps to do that for either NTFS or ext4 partitions.
       
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

And you may need to set ownership & permissions if ext4. NTFS is autoset in mounting and cannot be changed.

This is a manual mount, if automounted use that mount point and just run chmod & chown commands:

        #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data
[http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942](http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942)

---

### Post by juntjoo2 on 2016-12-06
Thank you. What are the differences between primary, logical, and extended partitions? Sorry. I got stuck there.

---

### Post by oldfred on 2016-12-06
MBR(msdos) back in early 1980s only had 4 partitions. Then they realized that users may want more, so they created a work around where one primary is converted to an extended partition and then you can have an unlimited number of logical partitions. Windows only boots from primary partitions, but Linux can boot from primary or logical with BIOS/MBR.

There now is the newer UEFI/gpt. The gpt partitioning allows 128 partitions by default. But Windows only boots in UEFI mode from gpt. Ubuntu can boot in either BIOS or UEFI from gpt if correct supporting partitions are created.

 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions old BIOS info:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by juntjoo2 on 2016-12-06
[ATTACH=CONFIG]272582[/ATTACH]

Lol, I can't even move information from one partition to another. Anyway, this is my result from parted -l. Thanks.

---

### Post by oldfred on 2016-12-06
Please post code directly by copying & pasting. And if longer use Code Tags which are easy to add in Forum's Advanced editor and the # icon.

It shows you have MBR(msdos) partitions. You have used all 4 primary, but sda4 is the extended holding your logical partitions.

---

### Post by juntjoo2 on 2016-12-06
Thanks. I used my camera because I can't get information in any form from the live CD environment to anywhere else. B can't connect to the internet either(no apparent reason) otherwise i would have pasted that way. Is the pic not clear in my last post?

So how would you get that space from my primary to the extended? I can shave off about 90gigs. And I just want to move it from one partition to the other. And I guess I can't delete one of those windows ones unless i don't want the windows but I want to keep it.

---

### Post by oldfred on 2016-12-06
What space?
I see every partition adjacent to every other partition.
Or do you have space inside your NTFS Windows partition?
If so, use Windows to shrink the NTFS, reboot immediately so it can run chkdsk. But do not make NTFS too small as it needs about 30% free inside it to work well.
Then you may be able to expand extended partition into unallocated.

---

### Post by juntjoo2 on 2016-12-06
The 174g is my main Ubuntu one and I can shrink that but that's where I get the error that doesn't give details I was talking about before. 

Just to recap I'm trying to out all my files on one partition keeping my os partitions small as possible. I shrank/shrunk the windows one and used that space to make this extra big one in there and I've been trying to do the same with my Ubuntu partition which I can about cut out half to move over. But I can't even complete the first step. It's just a general error with the details basically listing the steps I couldn't take(Shrink Ubuntu partition, create partition from empty space)

Windows are NTFS and Linux ext4 by default. So I've never touched a y of that

---

### Post by oldfred on 2016-12-06
Are you running only from live installer?
What version of Windows? If Windows 8 or later is its fast start up off? That would prevent gparted from correctly seeing it.

What brand/model system?
Are you connecting with hard wired Ethernet? Some wireless needs to download drivers that are not in live installer.

---

### Post by juntjoo2 on 2016-12-06
> **oldfred said:**
> Are you running only from live installer?
What version of Windows? If Windows 8 or later is its fast start up off? That would prevent gparted from correctly seeing it.

What brand/model system?
Are you connecting with hard wired Ethernet? Some wireless needs to download drivers that are not in live installer.

I thought the only way to use gparted to mess with the partitions was to use from outside the partitions you're modifying hence live cd(?)

Windows 10.

It's an older acer laptop and I'm connected wirelessly but I don't need to connect to the internet with the CD, my Ubuntu installation is working great so never mind that. I only need to be able to modify these partitions.

---

### Post by oldfred on 2016-12-06
It would be a bit easier for us to help you if live installer connected to Internet, so you could post more details easily.

Is Windows 10 fast start up off?
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

### Post by juntjoo2 on 2016-12-07
> **oldfred said:**
> It would be a bit easier for us to help you if live installer connected to Internet, so you could post more details easily.

Is Windows 10 fast start up off?
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

Not sure why I would need the live installer to see my windows partition. Thanks

I have what I thought I read to be the system that allows for more partitions being the latest Windows 10 unless i read wrong. Also, fast-boot, you think if I turn that off I'll be able to shrink my unbuntu os partition without these errors? Sorry. I'm a little confused. Or a lot

---

### Post by oldfred on 2016-12-07
Windows 10 in BIOS/MBR mode is no different than Windows 7. MBR restricts the number of primary partitions to 4, but then you can have one of the 4 primary as the extended and an unlimited number of logical.

Only if a newer computer with UEFI can you then install in UEFI boot mode and Windows by default uses the newer gpt partitioning.

If you have a fast boot setting in BIOS/UEFI, is it then a newer system?
Fast start up in Windows is different than fast boot in UEFI.

---

### Post by juntjoo2 on 2016-12-07
Almost understanding what you've been telling me. What's the difference between logical and primary and extended and how do I determine which of these my partitions are? Gparted doesn't appear to have a column for info related to that nor do I find anything after right clicking then "information" is there anything. Thanks

---

### Post by oldfred on 2016-12-07
Your partition table in Post #7 shows the primary, extended & logical partitions.
Primary partitions with MBR are always 1 thru 4, and logical partitions always start at 5. You do not have to use all 4 primary to have logical partition. You can make sda3 the extended and the the next partition inside sda3 is sda5 with no sda4. All logical partitions must be inside the extended when looking at the sector detail. And partitions do not have to be in order from left to right in view from gparted.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions#Additional_Notes_on_Partitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions#Additional_Notes_on_Partitions)

[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by juntjoo2 on 2016-12-07
I'm sorry. Idk what the difference of logical primary and extended are. I want to move space from one partition to another. Where do I start to accomplish this? Thanks

---

### Post by oldfred on 2016-12-07
I do not know if you remember the slide puzzles, where you move little squares around. Those were 2D.
You have a one D slide puzzle.

You have to shrink a partition, if Windows use NTFS and if Linux use gparted.
In most cases that unallocated space is then not next to where you want it. So you have to start moving partitions around. Since any power failure or interruption will totally corrupt system, you must have good backups. But I have moved partitions without issue.

If you make unallocated inside an extended partition you have to move it to the beginning or end of extended partition and then shrink extended partition to move unallocated outside the extended partition. You may then have to move primary partitions to have unallocated next to partition you want to expand. Always better to expand right as a move left & then expand right is another move with the risk of interruption again.

       Shrinking a Windows Vista/7/8 partition is best done in Windows. But do not create new partitions with Windows.
[URL="http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/"]http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/
[/URL]
 Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition) 

[URL="http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/"]
[/URL]

---

### Post by juntjoo2 on 2016-12-08
Thanks old Fred. I get what you're saying, most of it but why wouldn't I be able to shrink my Ubuntu partition?
[IMG]http://img-cdn.filefactory.com/embed/xl/1ogx5i7tkwyh.jpg[/IMG]
[IMG]http://img-cdn.filefactory.com/embed/xl/z9k2ennihkp.jpg[/IMG][IMG]http://img-cdn.filefactory.com/embed/xl/3b9zin7exljn.jpg[/IMG]
 [IMG]http://img-cdn.filefactory.com/embed/xl/77b1ud0i7tbh.jpg[/IMG]

---

### Post by oldfred on 2016-12-08
You show swap still mounted. Little key icon.
And then any mounted partition inside the extended partition in effect mounts the entire extended partition, so no changes allowed.

If you unmount swap with swap off, or right click in gparted it then should work.

---

### Post by juntjoo2 on 2016-12-09
old Fred, thanks a lot for sticking around buddy.  That worked and it should have worked two pages back as I remember unlocking those partitions before.  Don't know how I missed it.  Anyway, shrunk, created partition, moved it over, then combined. Done.

---

### Post by oldfred on 2016-12-09
Glad you got it to work.

---

