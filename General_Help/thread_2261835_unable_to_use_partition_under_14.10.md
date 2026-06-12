---
title: "unable to use partition under 14.10"
date: 2015-01-21
forum: General Help
---

### Post by eugen-koslowski on 2015-01-21
hey,

I previously installed ubuntu on my ideapad u410. I installed it on the 32gb ssd and wanted to use the big plate for data storage, but somehow i cannot copy files on it although it is connected. i tried to google it, but did not find any answers. 

thanks!

---

### Post by yancek on 2015-01-21
What exactly are you referring to with "big plate"?  Does this mean another hard drive, internal or external?  What's on it?  Any partitions with filesystems?  With it attached post the output of the two commands below:

sudo fdisk -l(Lower Case Letter L)
sudo df -h

---

### Post by eugen-koslowski on 2015-01-21
Disk /dev/sda: 29,8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe7ffe5c5

Device     Boot  Start      End  Sectors  Size Id Type
/dev/sda1  *      2048   499711   497664  243M 83 Linux
/dev/sda2       501758 62531583 62029826 29,6G  5 Extended
/dev/sda5       501760 62531583 62029824 29,6G 8e Linux LVM

Disk /dev/sdb: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8B2EB7CA-68F1-4172-B32B-8609B2031910

Device        Start       End   Sectors   Size Type
/dev/sdb1      2048  16001023  15998976   7,6G Linux swap
/dev/sdb2  16001024 976773119 960772096 458,1G Linux filesystem

Disk /dev/mapper/ubuntu--vg-root: 21,7 GiB, 23307747328 bytes, 45522944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/ubuntu--vg-swap_1: 7,9 GiB, 8447328256 bytes, 16498688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Dateisystem                 Größe Benutzt Verf. Verw% Eingehängt auf
/dev/mapper/ubuntu--vg-root   22G    9,0G   12G   45% /
none                         4,0K       0  4,0K    0% /sys/fs/cgroup
udev                         3,9G    4,0K  3,9G    1% /dev
tmpfs                        796M    1,3M  795M    1% /run
none                         5,0M    4,0K  5,0M    1% /run/lock
none                         3,9G    524K  3,9G    1% /run/shm
none                         100M     64K  100M    1% /run/user
/dev/sda1                    236M    156M   68M   70% /boot

---

### Post by eugen-koslowski on 2015-01-21
when i open disks, i see a small zzZZzzZZ symbol next to the partition

---

### Post by oldfred on 2015-01-21
You are showing a LVM or LVM with encryption install on sda. 
Is that what you wanted?
Drive is also configured as MBR(msdos) not gpt, where sdb is gpt partitioned.

Is then sdb2, just a data partition?
You may auto mount with Nautilus by click on it, but probably do not have ownership nor permission to use it. You need to give yourself ownership & permission.

And it may be better to add to fstab if an internal drive so it is always mounted.
       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)


            [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


If mounted unmount:
       #if not known to list partitions, change sdb2 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sdb2 /mnt/data
#where sdb2 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

    
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by eugen-koslowski on 2015-01-22
yes i guess i chose LVM at the installation. i thought it's safer or something. isn't there a simpler option?

---

### Post by oldfred on 2015-01-22
Standard install is just / (root) and swap. But if a very large drive better to keep / at 20 or 25GB and have a separate /home or data partition. 
With your SSD you then can have /home or the data partition(s) on the hard drive.

I also do suggest gpt, but it is not required.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by eugen-koslowski on 2015-01-23
i guess the problem is that i don't have root permissions. how can I gain it?

---

### Post by oldfred on 2015-01-23
sudo

       [URL="http://xkcd.com/149/"]http://xkcd.com/149/

[/URL]
 [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

[URL="http://xkcd.com/149/"]
[/URL]

---

### Post by eugen-koslowski on 2015-01-24
hey guys,

I just formatted my partition under GPARTED to FAT32 and now it works!

---

### Post by oldfred on 2015-01-24
Ubuntu does not work from FAT32 except for live installer.
UEFI does require a FAT32 partition for UEFI boot with both Windows & Ubuntu.

---

### Post by oldos2er on 2015-01-24
Moved to General Help.

---

