---
title: "USB only available to root"
date: 2017-11-24
forum: General Help
---

### Post by makem2 on 2017-11-24
When I plug in a USB stick I am unable to write to it. It is owned by root and the only way to make it usable by me is to chown it.

I am using xubuntu 16.04. Any advice available?

EDIT: I have noticed that the usb is writable if it is formatted in windows. If I format it with gparted it it owned by root and no longer available to me.

---

### Post by ajgreeny on 2017-11-24
With it attached show us the output in terminal of ```
sudo parted -l
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by makem2 on 2017-11-24
Result of [COLOR=#000000][FONT=&amp]sudo parted -l after formatting with gparted:

[/FONT][/COLOR]```
makem@ssdTOSH:~$ sudo parted -l
Model: ATA OCZ-VECTOR180 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  250MB   249MB   fat32                 boot, esp
 2      250MB   20.7GB  20.5GB  ext4
 3      20.7GB  123GB   102GB   ext4
 4      123GB   125GB   2048MB  linux-swap(v1)
 5      125GB   240GB   115GB   ext4




Model: ATA TOSHIBA MQ02ABD1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1075MB  1074MB  ntfs         Basic data partition          hidden, diag
 2      1075MB  1180MB  105MB   fat32        EFI system partition          boot, esp
 3      1180MB  1314MB  134MB   fat32        Microsoft reserved partition  msftres
 4      1314MB  81.6GB  80.3GB  ntfs         Basic data partition          msftdata
 5      81.6GB  82.6GB  1005MB  ntfs                                       hidden, diag
 6      82.7GB  980GB   898GB   ntfs         Basic data partition          msftdata
 7      986GB   987GB   500MB   ntfs                                       hidden, diag
 8      987GB   1000GB  13.2GB  ntfs         Basic data partition          hidden, diag




Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  16.0GB  16.0GB  fat32              msftdata




makem@ssdTOSH:~$ 



```

Result of [COLOR=#000000][FONT=&amp]sudo parted -l after formatting with windows:
[/FONT][/COLOR]
```

makem@ssdTOSH:~$ sudo parted -l
[sudo] password for makem: 
Model: ATA OCZ-VECTOR180 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  250MB   249MB   fat32                 boot, esp
 2      250MB   20.7GB  20.5GB  ext4
 3      20.7GB  123GB   102GB   ext4
 4      123GB   125GB   2048MB  linux-swap(v1)
 5      125GB   240GB   115GB   ext4




Model: ATA TOSHIBA MQ02ABD1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1075MB  1074MB  ntfs         Basic data partition          hidden, diag
 2      1075MB  1180MB  105MB   fat32        EFI system partition          boot, esp
 3      1180MB  1314MB  134MB   fat32        Microsoft reserved partition  msftres
 4      1314MB  81.6GB  80.3GB  ntfs         Basic data partition          msftdata
 5      81.6GB  82.6GB  1005MB  ntfs                                       hidden, diag
 6      82.7GB  980GB   898GB   ntfs         Basic data partition          msftdata
 7      986GB   987GB   500MB   ntfs                                       hidden, diag
 8      987GB   1000GB  13.2GB  ntfs         Basic data partition          hidden, diag




Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  16.0GB  16.0GB  fat32              msftdata




makem@ssdTOSH:~$

```

---

