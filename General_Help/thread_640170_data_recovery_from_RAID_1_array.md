---
title: "data recovery from RAID 1 array"
date: 2007-12-13
forum: General Help
---

### Post by Ndyanabo on 2007-12-13
I'm a noob who tried to get fancy with a simple software RAID 1 array for backup. I've had some problems, and now I need help recovering all the data saved on the array.

I used two new drives. It ran ok for a while, but then I started getting problems at startup, and it kept on asking me to run the fsck utility, which I did, repeatedly allowing it to correct many inode errors. Finally, it just stopped mounting all together. Odd, it now has an ext2 filesystem, even though I created it as ext3.
 
There is about 255 gig of data involved. Both HDs on the RAID array are 400 gig, and each have just one partition.
I have an empty 500 gig HD to recover the data to.


Here's what I get when I try to mount the array:

```
$ sudo mount -t ext2 /dev/md0 /media/mombasa
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

then if I try to mount one disk on its own:

```
$ sudo mount /dev/sdb1 /media/temp
mount: unknown filesystem type 'linux_raid_member'
```

That raises an interesting question for me: How do you take one hard drive out of a raid 1 array and mount it on its own like a normal disk?  


Basically, I followed the advice from this page on data recovery:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Testdisk:
In testdisk, I can flip through the directories and see that some of my data is there. That gives me a lot of confidence that my data is recoverable.

Perhaps I'm just not using Testdisk correctly (even though its supposed to be idiot-proof), but I haven't been about to mount my drive after playing with it.


I ran ddrescue to create an image:
```
sudo ddrescue -r 3 C /dev/sdb1 /media/jabbar/image logfile
```

This produced an 400 gig file "image", which then I tried to mount with Foremost, but that returned an error. I thought that Foremost would mount the image but instead I think it tried to write the data. However, I didn't have enough room on the empty hard drive to have both the image and the new (re)written data, so Foremost returned an error.

I deleted that file and and ran ddrescue again, :
```
ddrescue -r3 /dev/sdb1 /dev/sdd1 logfile
```

then:
```
e2fsck -v -f /dev/sdd1
```
which did a lot of inode repairs

followed by:
```
sudo mount -t ext2 -o ro /dev/sdd1 /media/temp
```
this just mounts sdd1, not the data image that ddrescue recovered to sdd1. Which makes sense to me, but I was just following the clear instructions on that data recovery page.

incidentally, I'm not sure where it wrote the data to the HD sdd1, but I;m sure its there, because when I mount sdd1, it's empty, but it says that only 99 gig are remaining.

of course, perhaps all of this is complicated by the fact that this is RAID. the data recovery page isn't really written for raid.


Thanks for looking. I don't know where to go from here. Does anyone have any suggestions for me?

---

### Post by donaldvr on 2008-01-10
I have had a similar problem.  I was merely experimenting with RAID 1.  I had an 80 GB external hard drive which I raided with an 80GB partition on the internal 120 GB drive.  It worked very well as an experiment.  However, it wasn't very practical.  After I disabled the raid array, my Ubunutu machine will not let me format or mount the individual drives.  I tried mounting the external drive on another Ubuntu system and got this error:  unknown filesystem type 'linux_raid_member'

I was able to finally get the USB drive working by first formatting it in NTFS on a Windows machine.  I supposed I could pysically remove the main 120 GB hard drive from my linux machine, place it in a Windows box and reformat the 80 GB partition, but there has to be an easier way.   Here is what happens when I try to mount the 80 GB partition of the internal drive: ```
 $ sudo mount /dev/hda5 ./backup
unknown filesystem type 'linux_raid_member'
```

I think this might actually be the exact same problem.  Any help would be greatly appreciated.

Thanks.

---

### Post by iwm on 2008-01-12
I also had the same problem,  I've solved it specifing the filesystem type:
mount -t ext3 /dev/sdd2 /media/old/data
(in my chase)

bye 
iWM

---

### Post by LarryJ2 on 2008-03-12
Thanks IWM

Just to clarify
After```
 sudo mkdir /media/sdd3
```

 if your attempt to retrieve your data off a partition, for example,  /dev/sdd3

```
$ sudo mount /dev/sdd3 /media/sdd3
```

results in 

```
mount: unknown filesystem type 'linux_raid_member'
```

then  

```
$ sudo mount -t ext3 /dev/sdd3 /media/sdd3
```

will mount your third partition of (in this case ) the fourth (or "d") harddisk.

You'll find your data in the directory  /media/sdd3.   (Phew!  thot I lost it all!!!)

---

### Post by mistermic on 2008-06-22
Thanks!  I had originally setup an 80G SATA drive with WinXP (/dev/sdc), a second 80G SATA drive with Ubuntu (/dev/sdd), then 2x200G IDE drives that were a mirrored samba share (/dev/sda & /dev/sdb)...Then I remembered that my sorta old ABIT IS7 mobo supported RAID, so I thought that I should mirror the 2 SATA drives for WinXP, and re-install Ubuntu on the 200G drive and mirror the second 200G drive to it, so then I'll have 80G of WinXP mirrored, and 200G of Ubuntu mirrored.  So I manually broke my mirror, successfully installed Ubuntu on /dev/sda, but wanted to copy data from the former samba share (/dev/sdb -- /dev/sdb1 specifically) and I was having trouble mounting, but this post worked for me!  :) After booting into the first Ubuntu OS and becoming root, I first ran "mkdir /share2 them mounted with command "mount -t ext3 /dev/sdb1 /share2", then I mounted /dev/sda3 (/media/disk) from Ubuntu from the "Places" drop down -> "Computer" --I could tell which one it was due to its size--and I'm copying my data over, disk to disk (much faster than copying via 100 MB network from my old Sun Ultra 5, 333 MHz CPU, running Solaris 10, that I'm retiring)...copying done, now to blow away /dev/sdb and mirror it to /dev/sda, then try to do some SATA mirroring for WinXP...

---

