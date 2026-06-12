---
title: "System partition(EXT4) resize(Extend) without format"
date: 2017-12-15
forum: General Help
---

### Post by upraity1995 on 2017-12-15
Hello there,

A long time ago, I installed Ubuntu 14.04 LTS alongside with Windows 10 on the same Laptop. At that time of Installation, I gave 20GB of HardDisk to system partition(EXT4) for Ubuntu and now I'm running out of space because I had to install and set up many required development softwares and environments that my work is totally dependent on them and I cannot afford to loose them all and doing a fresh install and then setting up everything again because It took a lot of efforts and time.

Here is how partitions looks like:
[  A  ] - [  B  ] - [  C  ] - [  D ] - [  E  ]

where,
A: Windows 10 partition (100GB) [NTFS]
B: other secondary partitions [NTFS]
C: Ubuntu System Partition (20GB) [EXT4]
D: *Unallocated Partition* (30GB)
E: Linux Swap

My requirement is just to resize(extend) the partition C from 20GB to 50GB after merging the unallocated partion to it in the most safest way possible without loosing the data.

I have visited a lot of forums and concluded that using a live USB/CD with same operating system installed and running it in live mode, we can use gparted or similar tools to be able to resize(shrink or extend) the partition without formatting the partition and also I did resizing of the secondary partitions with success without loosing data. But in those cases, there were either FAT32 or NTFS partition type.

I would like to be cleared about my doubts that whether the resizing of EXT4 partition type is same as of NTFS type, is this also possible with EXT4 to extend the partition without loosing the data as NTFS? and also I would like to know if there could be a case where Ubuntu uses some kind of locking functionality for system partition size and If I go extending the partition, I will end up with a corrupted ubuntu OS?

---

### Post by oldfred on 2017-12-15
Any system change has risks, so you must have backups of both Windows & your Linux partition.
Some like an Image backup with Clonezilla.
 [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 

I prefer to backup my data, /home, list of installed applications and some settings in /etc. I normally just copy any file I manually edit in /etc into /home so it gets backed up. I use rsync to copy to another drive, or flash drives. I also copy most critical data to DVDs, regularly.

Yes, you can resize ext4 partitions and generally it works without issue. It works too well as even though we know we need backups, we may do a change without updating backup before hand and that is the one time it does not work. It must have a built in check that if you have not done a backup that is the time it does not work. 
Unallocated must be next to ext4 partition. And if the 35 year old MBR(msdos) must be inside the extended partition if the ext4 partition is inside the extended partition. If newer gpt it just needs to be adjacent. If just expanding right, it will do the update very quickly. But if a move left is required, it has  to copy all data and that can take a long time. Any interruption or power failure totally corrupts data and then you are glad you have your backup.

I normally have 25GB for / (root) partition and my 16.04 is using about 11GB of the 25. But I have all data in a separate ext4 partition mounted as /mnt/data and all folders linked into /home. My /home is less than 2GB of the total 11GB. I do houseclean regularly.


 Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
[https://gparted.org/news.php](https://gparted.org/news.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by yancek on 2017-12-15
It should work but, the info you posted isn't detailed enough for anyone to give a conclusive answer so boot Ubuntu and run:  sudo fdisk -l(Lower Case Letter L in command) and post the output here.  Or, you can post an image of GParted with info on the drive.  As pointed out above, to extend a partition to unallocated space, the unallocated space needs to be adjacent to or contiguous with the partition you want to extend.  And yes, you need to use GParted on the live usb.

---

