---
title: "Can't mount external hard disk"
date: 2012-11-26
forum: General Help
---

### Post by David McCoy on 2012-11-26
Hey everyone, 

I need to move some files to my external before switching to windows.  My Asus EEE netbook won't boot after the 12.10 update and I can only boot to console.  I just can't use Linux here in Africa (I'm a Peace Corps Volunteer).  Unfortunately when I do: 

sudo fdisk -l

I get: WARNING: (GUID PARTITION TABLE) detected on '/dev/sdb'! The util fdisk doesn't support GPT.  Use GNU Parted.  *This is for my 1000g external. 

I've tried: sudo mount /dev/sdb /mnt/point
but Iget 
EXT4-fs (sdb): VFS: Can't find ext4 filesystem
FAT-fs (sdb): bogus number of reserved sectors
mount: you must specify the filesystem type

So I go to root: sudo -i, then parted to get ito GNUparted. 

Type help  but I see nothing that says how to mount the harddrive.  Literally all I need to do is mount the harddrive to mnt/point so I can move some files that weren't backed up over to my harddisk because this new Ubuntu  is to tweaky and windows is just want I need to switch to while I'm serving over here and don't have good internet.  

Anyone have any ideas, I would REALLY appreciate the help.

---

### Post by ajgreeny on 2012-11-26
Try **sudo parted -l** to list your partitions as I show below from my machine
```
sudo parted -l
[sudo] password for *user*: 
Model: ATA Maxtor 6B160P0 (scsi)
Disk /dev/sda: 164GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  10.7GB  10.7GB  primary   ext4            boot
 2      10.7GB  162GB   151GB   primary   ext4
 4      162GB   164GB   2147MB  extended
 5      162GB   164GB   2147MB  logical   linux-swap(v1)


Model: ATA Maxtor 6E040L0 (scsi)
Disk /dev/sdb: 41.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1048kB  41.1GB  41.1GB  extended
 5      8225kB  10.5GB  10.5GB  logical   ext4
 6      10.5GB  20.7GB  10.3GB  logical   ext4
 7      20.7GB  31.0GB  10.3GB  logical   ext4
 8      31.0GB  41.1GB  10.1GB  logical   ext4

```
This will show all your partitions with their size and type and you can then mount whatever you wish with the usual cli command.

---

### Post by dannyboy79 on 2012-11-26
if sdb only has 1 partition, then you need to specify that. so it would be
```
sudo mount /dev/sdb1 /mnt/foldername
```

---

