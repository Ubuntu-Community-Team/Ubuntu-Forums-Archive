---
title: "Help with gparted"
date: 2018-04-28
forum: General Help
---

### Post by jacko777 on 2018-04-28
I am running Ubuntu 16.04. I tried downloading a 1.8GB file but it kept stopping around 700~MB.  I asked before about no room left on "/" the help I got was fantastic.  I went through Gparted and expanded my sectors. (sda1, sda2, sda3...) but things still didn't work.
From there I went into the files on the left vertical quick launch.  There I found a place simply called "Computer".  That showed me there was only 700~MB free.  So I figured rightly or wrongly that this was the problem.  Question:  How do I expand this area.?  Looking in Gparted there is no area called just "computer".  Might this be on another drive.?  I ask this because I have 3 HDD's.  The original 500GB a 1TB and a 2TB drive.  THere is stacks of spare on the sda drive.

Regards,  Rod.

---

### Post by deadflowr on 2018-04-28
post back
```
sudo parted -l
df -h
```
those are two separate commands.
the first will show the partitioning layout.
And the second will show the current disk usage and which partitions are in use and where in the file system hierarchy.

*Computer* is usually a general term for the main root file system in use.

---

### Post by jacko777 on 2018-04-28
Thank you for that deadflower, being rather new to ubuntu I will enclose my findings.
```
rod@rod:~$ sudo parted -l
[sudo] password for rod: 
Model: ATA WDC WD20EZRZ-00Z (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  50.4GB  50.4GB  primary   ext2
 2      50.4GB  150GB   100GB   extended
 5      50.4GB  125GB   74.2GB  logical   ext4
 3      255GB   675GB   420GB   primary   ext4
 4      675GB   1054GB  379GB   primary   ext4


Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  3984MB  extended
 5      496GB   500GB  3984MB  logical   linux-swap(v1)


Model: Seagate Expansion (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB


rod@rod:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.8G     0  1.8G   0% /dev
tmpfs           366M  5.9M  360M   2% /run
/dev/sda1        47G   44G  646M  99% /
tmpfs           1.8G   20M  1.8G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.8G     0  1.8G   0% /sys/fs/cgroup
tmpfs           366M   76K  366M   1% /run/user/1000
/dev/sdc2       347G  4.6G  342G   2% /media/rod/327FB25D62E5FFA1
/dev/sdc1       812G   79G  734G  10% /media/rod/22DB2D983C6EF1EA
/dev/sda3       385G   71M  365G   1% /media/rod/Home
/dev/sda4       348G  171M  330G   1% /media/rod/d9929752-3aa1-4909-b58a-7503850f2837
/dev/sda5        68G  156M   65G   1% /media/rod/d9929752-3aa1-4909-b58a-7503850f28371
/dev/sdb1       455G   46G  387G  11% /media/rod/cbb1054b-6a1d-4de4-a949-23b389a29d7d
rod@rod:~$ 

```

I hope you are able to figure out where things are going wrong, and how to get it right..

---

### Post by Dennis N on 2018-04-28
Since sda1 (your root partition) is 99% full, you would consider either:

1) making the partition bigger
2) looking for your files that could be deleted or moved elsewhere (like to one of the external disks you have mounted under /media/rod). The 99% usage figure includes your home folder.

In this case, expanding sda1 is difficult since there is no free space after it. So I would persue option 2. Disk Usage Analyzer tool can help you see where and what those files might be so you can take action. In particuar, media files take up lots of room.

---

### Post by yancek on 2018-04-28
sda3 and sda4 are much larger partitions both of which are practically empty so I would agree that copying data there would be the simplest.  Copy personal data from your /home/rod directory.

sda3 shows as /media/rod/Home.  Were you trying to create a separate /home partition?

---

### Post by jacko777 on 2018-04-28
Thank you Dennis N, I will hunt for Disk Usage Analyzer and find what can be moved without mucking up my files or data.
In answer to yancek, yes I was trying to make a separate /home partition, I know very little about these parts of ubuntu, so any attempt I make to do something looks terribly amateurish to the people who understand these things.  What I need on these things is a step by step directions so that I might understand what to do next, having said that I do understand that with all the people looking for help, it is hard to take time out to write a novel about do this first followed by, etc...
Thanks both, I will try out both suggestions.
Rod.

---

### Post by Dennis N on 2018-04-28
Is ATA WDC WD5000AAKS-0 (scsi) an internal drive? If so, it's similar to my setup (2 internal drives, one SSD and one HDD).

Instead of a separate home partition, I use the second drive (HDD) just for data and mount it at startup so it is always available. And if I install a new OS on the first drive, the data remains safe on the 2nd drive. I still have a regular home folder on the first drive (SSD), but it is mostly empty, and only important for the configuration files that applications like to place in there. 

Data drive is mounted at **/mnt/data** at startup using an entry in **/etc/fstab**

I just bookmark several locations on the data drive in the file manager side pane to easily access places on it when browsing, saving or loading files.

Something to think about.

---

### Post by oldfred on 2018-04-28
If you want to move /home, this has step by step instructions.
If issues with any step post, probably better in a new thread with moving home in title.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

But I am just like Dennis N. I have /mnt/data as a large data partition. 
I primarily use that as I have more than one Ubuntu install. Do not want shared /home as I may want different settins or experiment with settings, but do want all my data in every install. So I have multiple / (root) partitions on SSD and large data partition on HDD (and maybe more / partitions).

---

### Post by jacko777 on 2018-04-29
Hello both Dennis N  and also oldfred.  The 2TB WDC5000AKS is an internal scsi drive.  I also have another internal scsi drive which is much smaller (~500G)
I followed the link that was the first one that oldfred showed.  I printed the file (6 pages) and I will get started after I clear up one more thing.
On the internal drive, sda, there is already 3 or is it 4 partitions, if I try to make another partition to move the home folder to I get an error message stating I may only create a maximum of 3 or 4 files.
This has me fazed a little, how to I create a new home folder to move my existing home folder...?
Always something to cause a catch 22 situation.
Any suggestions would be gratefully accepted.  Thank you all who have helped so far.

Rod.

---

### Post by oldfred on 2018-04-29
With the now 35 year old MBR(msdos) partitioning you can only have 4 primary partitions.
They realized that was a major limit so you can convert one primary partition to an extended partition which acts like a container for logical partitions. You can have an unlimited number of logical  partitions, but only in one extended partition per device.

Newer UEFI systems use gpt. And you can use gpt with BIOS boot if only using Ubuntu, but Windows only boots in the newer UEFI mode from gpt.
I started converting drives to gpt back in 2010. All new or totally repartitioned drives became gpt. Only MBR drive I may have is a small flash drive. 

Post this:
sudo parted -l

If you have one primary partition with no or little data, you can back that up, convert to an extended and add logical partitions inside the extended.
       MBR(for BIOS) or gpt(for UEFI) partitions:
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu) 

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by jacko777 on 2018-04-30
Hello oldfred, I hope I get this right..
[code] rod@rod:~$ sudo parted -l
Model: ATA WDC WD20EZRZ-00Z (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  50.4GB  50.4GB  primary   ext2
 2      50.4GB  150GB   100GB   extended
 5      50.4GB  125GB   74.2GB  logical   ext4
 3      255GB   675GB   420GB   primary   ext4
 4      675GB   1054GB  379GB   primary   ext4


Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  3984MB  extended
 5      496GB   500GB  3984MB  logical   linux-swap(v1)


Model: Seagate Expansion (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB


rod@rod:~$ 

[code]

---

### Post by oldfred on 2018-04-30
Your Seagate shows this:
Partition Table: loop

Which is not either MBR(msdos) nor gpt(GUID) partitioning.
It looks like you did not partition drive, but just formatted it like a SuperFloppy drive.
Most Linux tools expect partitions and do not work well with just a formatted drive.
There is no way to convert loop to actual partitions. If you can mount it, backup all data and then partition drive.

---

### Post by jacko777 on 2018-05-01
Hello again oldfred, the 1TB disk marked loop is my external backup drive.  It only contains backups of my weekly schedule and does no hold any stand alone programs.
Thanks for that link, there is a lot of heavy reading there (which I haven't read yet) and for an old bloke like me, although relatively new to ubuntu, it might take some time to digest.
Rather like some of my wife's cooking...ooops, didn't see her standing behind me.

Correct me if I'm wrong, but it looks like I will have to save the contents of the 'home' directory to a thumb drive? then remove the partition, add it to part of the vacant area in the 2 TB drive format it and copy the home directory back into the new and larger partition.???

Regards,
Rod

---

### Post by oldfred on 2018-05-01
It depends on where you want /home partition?
But in all cases best to have good backups of /home.

Post these also:
       lsblk -f 
cat /etc/fstab

---

### Post by jacko777 on 2018-05-01
OK oldfred, here are the results.

```

rod@rod:~$ lsblk -f 
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sdb                                                      
&#9500;&#9472;sdb2                                                   
&#9500;&#9472;sdb5 swap         eb6794de-a152-4fa5-8b63-4bd7248b16f0 [SWAP]
&#9492;&#9472;sdb1 ext4         cbb1054b-6a1d-4de4-a949-23b389a29d7d 
sdc                                                      
&#9500;&#9472;sdc2 ntfs         327FB25D62E5FFA1                     /media/rod/327FB25D62E5
&#9492;&#9472;sdc1 ntfs         22DB2D983C6EF1EA                     /media/rod/22DB2D983C6E
sda                                                      
&#9500;&#9472;sda4 ext4         d9929752-3aa1-4909-b58a-7503850f2837 
&#9500;&#9472;sda2                                                   
&#9500;&#9472;sda5 ext4         d9929752-3aa1-4909-b58a-7503850f2837 
&#9500;&#9472;sda3 ext4   Home  b4293086-dc3f-41fc-b628-085955268d46 
&#9492;&#9472;sda1 ext2         0ef3f17d-7331-49e8-a125-11616196ae5f /
sr1                                                      
rod@rod:~$ 


```
```

rod@rod:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0ef3f17d-7331-49e8-a125-11616196ae5f /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1559ead9-3f25-4b3d-9894-e9deb7c9b14a none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=eb6794de-a152-4fa5-8b63-4bd7248b16f0 none            swap    sw              0       0
/dev/disk/by-id/ata-TSSTcorp_CDDVDW_SH-222BB_R8SN6GAC4003GB /mnt/ata-TSSTcorp_CDDVDW_SH-222BB_R8SN6GAC4003GB auto nosuid,nodev,nofail,x-gvfs-show 0 0
rod@rod:~$ 

```

I hope this helps sort out my problem, thank you for your persistence.
Rod

---

### Post by Dennis N on 2018-05-01
> it looks like I will have to save the contents of the 'home' directory to a thumb drive? then remove the partition, add it to part of the vacant area in the 2 TB drive format it and copy the home directory back into the new and larger partition.???

Seems like a lot of extra work. If I may offer a suggestion:

Why not just mount sda3 (your intended home?) at startup to your root filesystem? Then you can browse, create folders, save, and load files there. You need another /etc/fstab entry to mount sda3 at startup. Or did you plan to store all your data on a separate drive? Your sda disk is huge with plenty of space. You could use another of the drives as backup.

Something to think about!

---

### Post by oldfred on 2018-05-01
Your sda4 & sda5 have same UUID?
That is not allowed, you need to change one or the other.

And using ext2 for / is not really recommended.
Some installs have a separate /boot partition that is ext2, but that is then a smaller partition with little activity, the addition of new kernels.

 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

---

### Post by jacko777 on 2018-05-04
Hello Dennis N, unfortunately I would need a step by step guide to do anything other than what I do normally,  
you would need to come to my home and hold me by the hand until it was done.  (No not literally)
Thank you for your input, I appreciate any and all help.

Regards,
Rod

---

### Post by jacko777 on 2018-05-04
Hello again oldfred, as you can see by what I have sent, I know extremely little about the innards of Linux.
I will include the two errors that surfaced when I tried your last post..

```

rod@rod:~$ sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
[sudo] password for rod: 
tune2fs 1.42.13 (17-May-2015)
tune2fs: No such file or directory while trying to open /dev/sdaX
Couldn't find valid filesystem superblock.
rod@rod:~$ sudo tune2fs -U random /dev/sdaX 
tune2fs 1.42.13 (17-May-2015)
tune2fs: No such file or directory while trying to open /dev/sdaX
Couldn't find valid filesystem superblock.
rod@rod:~$

```

---

### Post by deadflowr on 2018-05-04
You need to replace the X in sdaX with one of the partition numbers you want/need to change the uuid for.

---

### Post by jacko777 on 2018-05-04
G'day deadflower,  I guess that proves I am hopeless at this operating system.  I will push on though.
The answer to the earlier turned up yet another lemon.

```
 
rod@rod:~$ sudo tune2fs /dev/sda1 -U numbergeneratedbyuuidgen
tune2fs 1.42.13 (17-May-2015)
tune2fs: Invalid UUID format

```

---

### Post by jacko777 on 2018-05-04
Also the other type...
```

rod@rod:~$ sudo tune2fs -U random /dev/sda1
tune2fs 1.42.13 (17-May-2015)

```

---

### Post by oldfred on 2018-05-04
Did you get a new UUID?

Post this:
lsblk -f

sudo tune2fs /dev/sda1 -U numbergeneratedbyuuidgen

Means you use uuidgen to create a new UUID and then use above command but with the number not the text,  to assign that UUID to the partition.
Best to copy & paste UUIDs.

---

### Post by jacko777 on 2018-05-05
Hello oldfred,
I am getting lost here at the moment, but here are the answers to the 2 items you asked me to include.
```
rod@rod:~$ lsblk -f
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sdb                                                      
&#9500;&#9472;sdb2                                                   
&#9500;&#9472;sdb5 swap         eb6794de-a152-4fa5-8b63-4bd7248b16f0 [SWAP]
&#9492;&#9472;sdb1 ext4         cbb1054b-6a1d-4de4-a949-23b389a29d7d 
sr0                                                      
sdc                                                      
&#9500;&#9472;sdc2 ntfs         327FB25D62E5FFA1                     /media/rod/327FB25D62E5
&#9492;&#9472;sdc1 ntfs         22DB2D983C6EF1EA                     /media/rod/22DB2D983C6E
sda                                                      
&#9500;&#9472;sda4 ext4         d9929752-3aa1-4909-b58a-7503850f2837 
&#9500;&#9472;sda2                                                   
&#9500;&#9472;sda5 ext4         d9929752-3aa1-4909-b58a-7503850f2837 
&#9500;&#9472;sda3 ext4   Home  b4293086-dc3f-41fc-b628-085955268d46 
&#9492;&#9472;sda1 ext2         b44ab6bf-372d-48f1-b45b-9edb646e898e /
sr1                                                      
rod@rod:~$ sudo tune2fs /dev/sda1 -U numbergeneratedbyuuidgen
[sudo] password for rod: 
tune2fs 1.42.13 (17-May-2015)
tune2fs: Invalid UUID format

rod@rod:~$ 

```

---

### Post by oldfred on 2018-05-05
You have to run uuidgen to get a new UUID, but that is just the number.
And then you have to use tune2fs to assign that number to your partition, either sda4 or sda5 as they still both have same UUID.

fred@Xenial_z97:~$ uuidgen
[COLOR=#ff0000]897781ac-050c-429f-b8ef-87b9301b00d7[/COLOR]  <-- you copy this (yours will be different) as it is the number generated by uuidgen
Use either sda4 or sda5 as they still have same UUID.
sudo tune2fs /dev/sda4 -U [COLOR=#ff0000]numbergeneratedbyuuidgen[/COLOR]

---

### Post by jacko777 on 2018-05-06
Hello again oldfred, sorry about the delay but somehow I messed something up badly.  I had no to get into ubuntu so I reinstalled it beside the old one. I will include the last test as you asked because things have again changed since I last sent you a message.

```
rod@rod:~$ lsblk -f
NAME   FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                         
&#9500;&#9472;sda1 ext2            b44ab6bf-372d-48f1-b45b-9edb646e898e 
&#9500;&#9472;sda2                                                      
&#9500;&#9472;sda3 ext4   Home     b4293086-dc3f-41fc-b628-085955268d46 
&#9500;&#9472;sda4 ext4            d9929752-3aa1-4909-b58a-7503850f2837 
&#9500;&#9472;sda5 ext4            d9929752-3aa1-4909-b58a-7503850f2837 
&#9500;&#9472;sda6 ext4            f5836cfd-a11d-4891-8741-7c7501deb89c /
&#9492;&#9472;sda7 swap            1310281b-2965-4759-bf4d-86ae256bedb6 [SWAP]
sdb                                                         
&#9500;&#9472;sdb1 ext4            cbb1054b-6a1d-4de4-a949-23b389a29d7d 
&#9500;&#9472;sdb2                                                      
&#9492;&#9472;sdb5 swap            eb6794de-a152-4fa5-8b63-4bd7248b16f0 
sdc                                                         
&#9500;&#9472;sdc1 ntfs            22DB2D983C6EF1EA                     /media/rod/22DB2D983
&#9492;&#9472;sdc2 ntfs            327FB25D62E5FFA1                     /media/rod/327FB25D6
sdd                                                         
&#9492;&#9472;sdd1 vfat   VERBATIM 5BAD-26E2                            /media/rod/VERBATIM
sr0                                                         
sr1                                                         
rod@rod:~$ sudo tune 2fs /dev/sda1 -U d9929752-3aa1-4909-b58a-7503850f2837
[sudo] password for rod: 
sudo: tune: command not found

```

Regards,
Rod

---

### Post by oldfred on 2018-05-06
These two are still the same, you have not changed the UUID of one or the other.

sda4 ext4            d9929752-3aa1-4909-b58a-7503850f2837 
&#9500;&#9472;sda5 ext4            d9929752-3aa1-4909-b58a-7503850f2837

---

### Post by jacko777 on 2018-05-07
Hello oldfred (if you haven't given up and tore your hair out), where am I going wrong with the tune2fs.... command.?
```
rod@rod:~$ tune2fs/dev/sda4 -U 2fbed22f-6238-482e-af83-9daaa16ab9f9
bash: tune2fs/dev/sda4: No such file or directory
rod@rod:~$ tune2fs/dev/sda 2fbed22f-6238-482e-af83-9daaa16ab9f9
bash: tune2fs/dev/sda: No such file or directory
rod@rod:~$ 

```

---

### Post by deadflowr on 2018-05-07
space
as in you need some space between tune2fs and /dev/sda4
it's reading it as one long command tune2fs/dvsda4 and not tune2fs /dev/sda4
also I think you need to run it with sudo.

---

### Post by oldfred on 2018-05-07
+1 on deadflowers suggestions.

Details on sudo, although in this case it has never worked for me. :)
 [http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by jacko777 on 2018-05-08
Thanks again to deadflwr and oldfred.  I have got the tune2fs data.  Could you now advise me how this helps in getting rid of one of the /dev/sda4 partitions please.  I know this is getting long winded now, but I appreciate your sticking with it to help me finally get the problem sorted.
```
rod@rod:~$ sudo tune2fs /dev/sda4
[sudo] password for rod: 
tune2fs 1.42.13 (17-May-2015)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
    [-i interval[d|m|w]] [-j] [-J journal_options] [-l]
    [-m reserved_blocks_percent] [-o [^]mount_options[,...]] [-p mmp_update_interval]
    [-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
    [-M last_mounted_dir] [-O [^]feature[,...]]
    [-Q quota_options]
    [-E extended-option[,...]] [-T last_check_time] [-U UUID]
    [ -I new_inode_size ] device
rod@rod:~$ 

```

regards,
Rod

---

### Post by deadflowr on 2018-05-08
Closer
try this
```
sudo tune2fs /dev/sda4 -U 2fbed22f-6238-482e-af83-9daaa16ab9f9
```
this was mostly right from [the previous post]("https://ubuntuforums.org/showthread.php?t=2076205&page=16&p=13764313#post13764313")
But notice that I've added the sudo and broke part the tune2fs and /dev/sda4 line.
This should give you the new uuid for /dev/sda4.

hope it makes more sense now.

---

### Post by oldfred on 2018-05-08
Once the duplicate UUID is gone, then gparted should work from live installer.

---

### Post by jacko777 on 2018-05-11
OK, I did a copy and paste this time, the following was the readout
```
rod@rod:~$ sudo tune2fs /dev/sda4 -U 2fbed22f-6238-482e-af83-9daaa16ab9f9
tune2fs 1.42.13 (17-May-2015)
rod@rod:~$ 
```

---

### Post by oldfred on 2018-05-11
Then did you double check that UUID is different?
And then does gparted work?

---

### Post by jacko777 on 2018-05-11
Sorry I forgot to put the test in my answer, I hope this gets me out of trouble..
```

rod@rod:~$ lsblk -f
NAME   FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                         
&#9500;&#9472;sda1 ext2            b44ab6bf-372d-48f1-b45b-9edb646e898e 
&#9500;&#9472;sda2                                                      
&#9500;&#9472;sda3 ext4   Home     b4293086-dc3f-41fc-b628-085955268d46 
&#9500;&#9472;sda4 ext4            2fbed22f-6238-482e-af83-9daaa16ab9f9 
&#9500;&#9472;sda5 ext4            d9929752-3aa1-4909-b58a-7503850f2837 
&#9500;&#9472;sda6 ext4            f5836cfd-a11d-4891-8741-7c7501deb89c /
&#9492;&#9472;sda7 swap            1310281b-2965-4759-bf4d-86ae256bedb6 [SWAP]
sdb                                                         
&#9500;&#9472;sdb1 ext4            cbb1054b-6a1d-4de4-a949-23b389a29d7d 
&#9500;&#9472;sdb2                                                      
&#9492;&#9472;sdb5 swap            eb6794de-a152-4fa5-8b63-4bd7248b16f0 
sdc                                                         
&#9500;&#9472;sdc1 ntfs            22DB2D983C6EF1EA                     /media/rod/22DB2D983
&#9492;&#9472;sdc2 ntfs            327FB25D62E5FFA1                     /media/rod/327FB25D6
sdd                                                         
&#9492;&#9472;sdd1 vfat   VERBATIM 5BAD-26E2                            /media/rod/VERBATIM
sr0                                                         
sr1                                                         
rod@rod:~$ 

```

---

### Post by oldfred on 2018-05-11
Does gparted now work?
I do not see any duplicates.

---

### Post by jacko777 on 2018-05-12
Hello oldfred, happy to report the gparted is working.  I have downloaded the ubuntu 18.04lts as a test, I burned the .ISO to a disk and booted from it OK.
This was the one thing I could never do before, so it worked a treat.
Again, thanks to yourself and deadflowr this issue is now complete.  I must now search for "solved" and mark the session closed.

Thank you both for your perseverance with an old bloke..

Kind regards,
Rod.

---

