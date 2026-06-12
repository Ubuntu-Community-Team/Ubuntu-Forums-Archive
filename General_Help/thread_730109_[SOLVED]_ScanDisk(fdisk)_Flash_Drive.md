---
title: "[SOLVED] ScanDisk(fdisk) Flash Drive"
date: 2008-03-20
forum: General Help
---

### Post by Rytron on 2008-03-20
Hi,
I want to use fdisk in Ubuntu to scan my flash drive.

I have used```
 sudo fdisk -l
```

but I dont know which device my flash drive is. My flash drive is 2GB FAT32

output-
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = 

cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d773d76

   Device Boot      Start         End      Blocks   Id  

System
/dev/sda1   *           1       21202   170305033+   7  HPFS/NTFS
/dev/sda2           21490       41872   163726447+   

5  Extended
/dev/sda3           41873       60801   152047192+  83  Linux
/dev/sda5           21490       41115   157645813+  

 7  HPFS/NTFS
/dev/sda6           41116       41872     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 2029 MB, 

2029518848 bytes
190 heads, 6 sectors/track, 3477 cylinders
Units = cylinders of 1140 * 512 = 583680 bytes
Disk identifier: 

0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3478     1981935+ 

  b  W95 FAT32
```

I know that this is the correct method:
```
sudo umount <device name>
sudo fsck.vfat <device name>
```

So I am thinking that the flash drive is 
```

/dev/sdb1
```

so I try:

```
[CODE][CODE]:~$ sudo fsck.vfat /dev/sdb1 dosfsck 2.11, 12 Mar 2005, FAT32, 
```

LFN[/CODE]

There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00

1) Copy 
original to backup
2) Copy backup to original
3) No action[/CODE]

Now I am not sure why it is saying boot sector. Am I going about this correctly? What do I do next?

Thank you.

---

### Post by nick_h on 2008-03-20
Yes, /dev/sdb1 is the partition you want.

You can check it with:
```
sudo fsck /dev/sdb1
```

---

