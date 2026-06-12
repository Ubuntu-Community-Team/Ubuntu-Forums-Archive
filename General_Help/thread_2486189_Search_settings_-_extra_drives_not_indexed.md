---
title: "Search settings - extra drives not indexed"
date: 2023-04-22
forum: General Help
---

### Post by faust99 on 2023-04-22
I've recently installed some extra storage in my desktop (HDD & SSD) but nautilus doesn't conduct searches there unless I specifically enter the directory. The activities overview doesn't search there either. I've adjusted the search settings to do so, but it hasn't worked. Am I missing something?

---

### Post by dragonfly41 on 2023-04-22
To the left of your screen is a docking panel showing all apps.
Right at the bottom are my several mounted SSD's. You can dive straight into each.

---

### Post by faust99 on 2023-04-22
Thanks, but that's not what I'm trying to do. I'd like those mounted SSD's - which are connected via a SATA rather than USB - to be part of the search results in the activities overview.

---

### Post by MAFoElffen on 2023-04-22
A search path in any File Manager, in any OS will search in the current folder and any subfolder. This is the way it works for Linux, Windows, UNIX, Android, MAC OSX, etc. 

It will not search in any parent folder or in any other drive. That is just the way that works.

---

### Post by faust99 on 2023-04-22
OK I see. If that's the case, what does the 'search locations' setting - in which you can add bookmarks - do? I've bookmarked the new drives and added the bookmarks to the search locations, but nothing's changed.

---

### Post by oldfred on 2023-04-22
If permanently installed, you need to add partitions to fstab.
Then settings can be remembered.

Post these in code tags (# in Forum's advanced editor):
sudo parted -l
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint

---

### Post by faust99 on 2023-04-22
Not sure if I've posted what you've asked for....the partitions I'd like to add are sdc6 and sdd1.

```
Model: ATA SPCC Solid State (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  106MB  105MB   fat32           EFI system partition          boot, esp
 2      106MB   123MB  16.8MB                  Microsoft reserved partition  msftres
 3      123MB   105GB  104GB   ntfs            Basic data partition          msftdata
 4      105GB   105GB  641MB   ntfs                                          hidden, diag
 5      105GB   136GB  30.8GB  ext4
 6      136GB   138GB  2000MB  linux-swap(v1)                                swap
 7      138GB   512GB  374GB   ext4


Model: ATA ST4000DM004-2U91 (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB  ext4


Model: ATA ST2000DM008-2UB1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  2000GB  2000GB  extended
 5      2097kB  500GB   500GB   logical   ext4
 6      500GB   2000GB  1500GB  logical   ext4


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4


Model: Seagate Expansion (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext4

```

```
NAME   FSTYPE   SIZE FSUSED LABEL        PARTLABEL                    MOUNTPOINT
sda           476.9G                                                  
&#9500;&#9472;sda1 vfat     100M    35M              EFI system partition         /boot/efi
&#9500;&#9472;sda2           16M                     Microsoft reserved partition 
&#9500;&#9472;sda3 ntfs    97.3G  79.3G              Basic data partition         /mnt/1E6C251C6C24EFE7
&#9500;&#9472;sda4 ntfs     611M 559.8M                                           /mnt/B4C6ED9FC6ED61DA
&#9500;&#9472;sda5 ext4    28.7G    20G                                           /
&#9500;&#9472;sda6 swap     1.9G                                                  [SWAP]
&#9492;&#9472;sda7 ext4   348.3G 301.7G                                           /home
sdb             3.6T                                                  
&#9492;&#9472;sdb1 ext4     3.6T        Backup                                    
sdc             1.8T                                                  
&#9500;&#9472;sdc1            1K                                                  
&#9500;&#9472;sdc5 ext4   465.7G 343.5G Albums                                    /mnt/83abb995-c944-49d1-a7a4-fe5375161fc4
&#9492;&#9472;sdc6 ext4     1.4T 144.6G Miles Smiles                              /mnt/871dcfed-a8a7-4ce4-b92b-7aaa58b094c3
sdd           465.8G                                                  
&#9492;&#9472;sdd1 ext4   465.8G 372.9G limak_2                                   /mnt/e0201941-c8a7-417a-9ae0-e4483efd9e9f
sde           931.5G                                                  
&#9492;&#9472;sde1 ext4   931.5G 869.2G bkp                                       /media/limak/bkp

```

---

### Post by oldfred on 2023-04-22
I would change Miles Smiles to Miles_Smiles. I stopped using spaces when I first installed Ubuntu as Linux requires work arounds for spaces. Just easier not to have them.

Umount the mounts by UUIDs.

add to fstab by label mounts
example
[https://ubuntuforums.org/showthread.php?t=2464668&p=14047676#post14047676Probably](https://ubuntuforums.org/showthread.php?t=2464668&p=14047676#post14047676Probably) better not to use albums, Miles_Smiles as both label & mount. I got into real trouble with data & Data, one as label & other as mount. 
You need to make the mount point in /mnt But also use mount that you understand.
sudo mkdir /mnt/XXXX

LABEL=Albums /mnt/XXXX ext4    nodev,nosuid,noatime,errors=remount-ro,nofail     0  1
LABEL=Miles_Smiles /mnt/YYYY ext4    nodev,nosuid,noatime,errors=remount-ro,nofail     0  1

You can then link folders in the partitions into /home if desired as mounts in /mnt do not normally appear in file browser.

---

