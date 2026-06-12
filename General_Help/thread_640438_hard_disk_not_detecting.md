---
title: "hard disk not detecting"
date: 2007-12-14
forum: General Help
---

### Post by irshan on 2007-12-14
i attched one of harddisk into my ubuntu machine to recover data but that is not detecting in my machine.so can u help me what would be the case and how can i recover my data from that harddisk.

---

### Post by frodon on 2007-12-14
What kind of disk is it ? sata , IDE, usb , ...

If it is an usb disk type the following command in a terminal and see if your disk is listed once you have connected it :
```
lsusb
```

---

### Post by danwood76 on 2007-12-14
When you say 'recover data' do you mean the disk is faulty and your trying to recover lost data?

Providing more insformation often leads to a better respnose!

---

### Post by irshan on 2007-12-16
it is a IDE 
the hard disk which is not working as a system but if it remove and put in to nother machine as slave then it is working i mean it is showing all partions in windows.but when attched in to ubuntu system the disk and it is partions not showing thus i coudnt recover data by ubuntu pls giv me a solutions.

---

### Post by frodon on 2007-12-17
We need some more details to help you, what type of filesystem, NTFS, FAT32 ?

When your disk plugged in and ubuntu launched type the following command in a terminal :
```
sudo fdisk -l 
```I think your disk is just not mounted by default, however i can't give you the command to add as i don't know your partition table neither the kind of file system you are using.

So please join the output of the "sudo fdisk -l" command in your next post so we will be able to give you the command to add in your fstab file and your partition will be mounted automatically.

---

### Post by irshan on 2007-12-17
NTFS file system
the partion of 2nd harddisk consist all NTFS file system.

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31793178

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9732    57689415    f  W95 Ext'd (LBA)
/dev/sda5            7651        9732    16723633+   7  HPFS/NTFS
/dev/sda6            2551        2563      104359+  83  Linux
/dev/sda7            2564        4985    19454683+  83  Linux
/dev/sda8            4986        5100      923706   82  Linux swap / Solaris
/dev/sda9            5101        7650    20482843+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b309b30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        9732    57689415    f  W95 Ext'd (LBA)
/dev/sdb5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sdb6            5101        7650    20482843+   7  HPFS/NTFS
/dev/sdb7            7651        9732    16723633+   7  HPFS/NTFS

---

### Post by frodon on 2007-12-17
Ok, then your disk is well recognized but just not mounted. Follow the instruction in the link below and it should good :
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c)

---

### Post by irshan on 2007-12-18
tanks lot for given a link and i went through that link and i followed the instruction but noting happen.if it is mounted the partitions should come to desktop but not happen like that. so could u help me further more

---

### Post by danwood76 on 2007-12-18
They will only appear on the desktop if mounted in the /media directrory.

What mount commands did you use?
(they will be like mount..... or ntfsmount etc)

---

### Post by frodon on 2007-12-18
If you are not too scared by editing things by hand you should use the "The manual way" part of the tutorial i gave you. It explains you how to edit you fstab file, once edited as needed just reboot.

For example if you would like to mount all the partitions of your second drive you would first create 4 directories in your /media folder, in command line that would make :
```
sudo mkdir -p /media/partition1
sudo mkdir -p /media/partition2
sudo mkdir -p /media/partition3
sudo mkdir -p /media/partition4
```

Then you would add the following lines at the end of your fstab file :
```
/dev/sdb1 /media/partition1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb5 /media/partition2 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb6 /media/partition3 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdb7 /media/partition4 ntfs-3g defaults,locale=en_US.utf8 0 0
```Then to get them mounted either reboot or typr in terminal :
```
sudo mount -a
```

---

### Post by irshan on 2007-12-18
stil not mounted, this is step what i fallowed accoding to link

han@han-desktop:~$ sudo mkdir -p /media/partition1
[sudo] password for han:
han@han-desktop:~$ sudo mkdir -p /media/partition2
han@han-desktop:~$ sudo mkdir -p /media/partition3
han@han-desktop:~$ sudo mkdir -p /media/partition4
han@han-desktop:~$ cd /media/
han@han-desktop:/media$ ls
cdrom   fedora  floppy0  partition1  partition3  sda1  sda6
cdrom0  floppy  linux    partition2  partition4  sda5  sda7
han@han-desktop:/media$ cd ..
han@han-desktop:/$ cd ..
han@han-desktop:/$ /dev/sdb1 /media/partition1 ntfs-3g defaults,locale=en_us.utf8 0 0
bash: /dev/sdb1: Permission denied
han@han-desktop:/$ media/partition1
bash: media/partition1: is a directory
han@han-desktop:/$ cd media/partition1
han@han-desktop:/media/partition1$ ls
han@han-desktop:/media/partition1$ cd /
han@han-desktop:/$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
han@han-desktop:/$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31793178

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9732    57689415    f  W95 Ext'd (LBA)
/dev/sda5            7651        9732    16723633+   7  HPFS/NTFS
/dev/sda6            2551        2563      104359+  83  Linux
/dev/sda7            2564        4985    19454683+  83  Linux
/dev/sda8            4986        5100      923706   82  Linux swap / Solaris
/dev/sda9            5101        7650    20482843+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b309b30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        9732    57689415    f  W95 Ext'd (LBA)
/dev/sdb5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sdb6            5101        7650    20482843+   7  HPFS/NTFS
/dev/sdb7            7651        9732    16723633+   7  HPFS/NTFS
han@han-desktop:/$ sudo fdisk -l |grep NTFS |awk '{print $1}'
/dev/sda1
/dev/sda5
/dev/sdb1
/dev/sdb5
/dev/sdb6
/dev/sdb7
han@han-desktop:/$ sudo cp /etc/fstab /etc/fstab.orig
han@han-desktop:/$ cd media/
han@han-desktop:/media$ ls
cdrom   fedora  floppy0  partition1  partition3  sda1  sda6
cdrom0  floppy  linux    partition2  partition4  sda5  sda7

---

### Post by frodon on 2007-12-18
No, the "dev/sdb1 /media/partition1 ntfs-3g defaults,locale=en_us.utf8 0 0" commands are to be added in your fstab files, these are not terminal commands at all.

To open your fstab file type in a terminal :
```
sudo gedit /etc/fstab
```

Then add at the end of the file the lines i gave you in my previous post and save the file then reboot or type "sudo mount -a".

---

### Post by vanadium on 2007-12-18
There is no need for the user to edit /etc/fstab if his aim is just to "recover data". He might remove the drive afterwards, or format it again. 

There are several partitions on your sdb drive, sdb1, 2, etc. (why do you need so many on a 80 GB disk?). In order to acces them, they must be individually mounted. I am showing the manual procedure to mount sdb1. It involves 1) creating a mount point (= empty directory), and 2) mounting the partition on it

sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1

If no output appears, the drive is mounted and its contents can be accessed (probably read-only for ntfs volumes) in /mnt/sdb1.

Any output indicates an error condition. It is common that ntfs partitions are not "clean" and need to be checked before they can mount. The safest way to check ntfs volumes is to do that in Windows, which you presumably have.

You need to include the partitions in /etc/fstab only when you plan to have the partitions permanently mounted in Ubuntu.

---

