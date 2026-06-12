---
title: "Lost partition after installing Windows 8"
date: 2014-08-06
forum: General Help
---

### Post by trudzki on 2014-08-06
Hello everyone.
I had 2 partititions under ext4 plus one partition controlled by NTFS. I have installed Windows 8 on NTFS and after this I have seen that there is only one partition with ext4. Howewer this partition now has size of both partition. Before this first ext4 partition had about 125 GB and second had 50 GB. As I said, now there is one partition, but with size 125+50=175 GB. And with 8 gb free. It seems that these partitions now are conjugated themseves. 

But I dont see files from second partition. TestDisk see only one Linux partition. 


```
sudo fdisk -l
```

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004d94d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046   460802047   230400001    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sda2   *   460802048   461006847      102400    7  HPFS/NTFS/exFAT
/dev/sda3       461006848   608462847    73728000    7  HPFS/NTFS/exFAT
/dev/sda4       617058304   625141759     4041728   82  Linux swap / Solaris
/dev/sda5       112642048   460802047   174080000   83  Linux
rs
Disk /dev/mmcblk0: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

```

And:```
 $ cat /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=5d520ff1-c5c4-49ad-9b2d-ea17ad99a19f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=e41fdabb-b110-442c-99a4-6a064d96d1e0 none            swap    sw              0       0


```

What should I do?

---

### Post by sudodus on 2014-08-06
Welcome to the Ubuntu Forums :-)

You have posted in a discussion forum. Do you want to discuss what happened, or do you want help to recover what is possible from your former two ext4 partitions? In that case maybe I should move your thread to a support forum.

Someone told me "Install the least intelligent system first". You might laugh at that, if you had not lost your data ...

Have you got any backup of your linux system or at least your personal files?

---

### Post by trudzki on 2014-08-06
I want to recover all my data. Unfortunately I have not backup. I had my backup, but in lost partition ;) 
It seems that "lost" partition is sda5, howewer in /etc/fstab "/ was on /dev/sda5 during installation"
I must explain something in addition to this. I had two linux partition - one for system - xUbuntu, second - for temporary files, backup from Windows. And this partition for temporary files had small amount of reserved disk space. So I think that this "lost partition" might be sda5, but I want be cafefull to prevent data loss. 
What I should do in this case?  Of course 
mount /dev/sda5 /mnt does not run

---

### Post by sudodus on 2014-08-06
If the data are important, it is a good idea to be careful and not use the drive, but instead clone it to another drive with ddrescue.

- Install a system to another drive, or make a persistent live USB drive. I suggest a USB pendrive.

- Boot from this USB pendrive.

- Install ***ddrescue*** and read the excellent info pages ```
info ddrescue
```

- Use ddrescue to make a cloned copy of the whole drive to an external drive of at least the same size. *Edit*: I mean drive in the linux meaning: whole disk.

- Then do the recover operations on the cloned copy. Save the recovered files to still another external drive that is big enough, maybe a USB hard disk drive.

I would start with ***Testdisk***, try a lot of things according to what you find via the internet. If still no luck I would try ***PhotoRec***. It can find the file content without help of a file system, but the file names are lost, and fragmented files will probably be damaged. This is a lot of hard work, but possible. I have done it (but only with a small number of files).

-o-

If you think it is not necessary or too expensive with several new drives, you can do the recovery directly from the original internal drive, but operations with Testdisk are risky. I think PhotoRec will only read from the source drive, so it should be less risky. Just make sure that you write the recovered files to the correct mounted target partition (in an external drive).

-o-

I'll move the thread to the [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331") Forum if you wish. I think more people will find it there so you can get more tips and advice.

---

### Post by trudzki on 2014-08-06
Ok,please, move this thread to General Help Forum

---

### Post by oldfred on 2014-08-06
Windows often does not correctly rewrite the Linux partitions in an extended partition. Best to have backup of partition table if installing Windows after Linux.

You show an extended partition and one logical inside it, but seem to also have space. I am wondering if current missing partition and sda5 were primary partitions?

 /dev/sda1            2046   460802047   230400001    5  Extended

   /dev/sda5       112642048   460802047   174080000   83  Linux

from 2046 to 112642048 looks like it could be or have been another partition.
But 2046 is unusual. All partition tools start partitions at 2048, which may be a separate issue? It could be that partition that started at 2048 was a primary and you do have to have a block or two before it for the start of the extended partition, so the start of the extended became 2046 to include the old primary as a logical?

Before doing anything make a backup of your partition table as it is now, just so if it gets worse you can get back.
      
 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Did you try deeper search with testdisk?

---

