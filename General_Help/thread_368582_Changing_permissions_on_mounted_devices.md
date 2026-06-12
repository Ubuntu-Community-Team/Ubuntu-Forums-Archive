---
title: "Changing permissions on mounted devices?"
date: 2007-02-23
forum: General Help
---

### Post by agiamba on 2007-02-23
Hi, I recently deleted a bunch of stuff from my external hard drive, yet it moves to the trash but I can't remove it. I've also had problems torrenting to the externalhd, as it says I don't have permission. I've opened it up and it says I have read-write permissions but not create-files/folders permission. I'm the only user of the computer, and the checkboxes there are disabled. Recommendations?

---

### Post by taurus on 2007-02-23
What is the filesystem on that harddrive and how do you mount it?

---

### Post by agiamba on 2007-02-24
it's fat32, and it just automatically mounts everytime I just plug it in. I do know some commands for mounting but if necessary, i'd love to learn more.

---

### Post by agiamba on 2007-03-02
bump-

---

### Post by taurus on 2007-03-02
What's the output of this command with the drive plugged in?

```
sudo fdisk -l
```

---

### Post by pirothezero on 2007-03-02
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

Might want to check out the ubuntuguide on that. Helped me with ntfs a while ago.

---

### Post by agiamba on 2007-03-03
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6516        9729    25816455    b  W95 FAT32
/dev/sda2   *           9        4852    38909430    7  HPFS/NTFS
/dev/sda3            4853        6254    11261565   83  Linux
/dev/sda4            6255        6515     2096482+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)

---

### Post by taurus on 2007-03-03
```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by agiamba on 2007-03-05
that did it, many thanks!!

---

