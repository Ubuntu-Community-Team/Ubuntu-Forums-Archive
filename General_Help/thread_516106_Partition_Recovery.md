---
title: "Partition Recovery"
date: 2007-08-02
forum: General Help
---

### Post by MikeM64 on 2007-08-02
Hello,

I have started my switch from windows over to ubuntu. I have a 160gb hd that is in 4 partitions:

/dev/sda
sda4: ext3 (98gb)
sda5: swap (2gb)
sda6: FAT32 BackupPartition (30gb)
sda7: NTFS Vista (15gb)

I decided to nuke my original windows partition (where sda4 & 5 are now) and leave the rest intact as they hold backups. So i run through the installer manually changing partitions to the way it is now. 
I go through a successful install, restart and begin installing essential applications (WINE, drivers, win apps), when I realize that only the NTFS partition is visible. I start searching and find that some how my fat32 partition got semi-corrupted. The partition table seems fine, but it says FS corrupted. I got all of my data off of the vista partition but my 30gb of backups are MIA. I start to work through TestDisk, parted, fdisk, and Vista recovery console to put the FAT partition into a readable state but it doesn't work.

I'm not sure whether I've missed anything (probably have) but I need to get at the FAT partition. I'll try anything, I just can't download any big (>100mb) live cds (2gb limit from sympatico).

Also, shouldn't an internal IDE hd be hda? I'm on an E7205 (Granite Bay P4) chipset (single drive) and it is recognized as sda.

My live cd is Ubuntu 7.04.

Thanks,
Mike.

---

### Post by be4truth on 2007-08-02
Is you partition mounted? You could make a folder in your mnt-partition. Paste the code into a shell.

```
sudo mkdir /mnt/temp
```

then 

```
sudo mount -t vfat  /dev/sda6 /mnt/temp
```

---

### Post by MikeM64 on 2007-08-03
I have already tried to mount the backup partition. After running the command it says FS corrupted.

Is there a way to force mount a partition?

Thanks,
Mike.

---

### Post by xzero1 on 2007-08-03
Why do you say the partition table is correct? Can you access the files on your backup partition using testdisk? You should be able to list the directory contents using testdisk. Have you modified in any way the partition table? Is the backup partition an extended partition?

---

### Post by az on 2007-08-03
> **MikeM64 said:**
> Hello,

I have started my switch from windows over to ubuntu. I have a 160gb hd that is in 4 partitions:

/dev/sda
sda4: ext3 (98gb)
sda5: swap (2gb)
sda6: FAT32 BackupPartition (30gb)
sda7: NTFS Vista (15gb)

I decided to nuke my original windows partition (where sda4 & 5 are now) and leave the rest intact as they hold backups. So i run through the installer manually changing partitions to the way it is now. 
I go through a successful install, restart and begin installing essential applications (WINE, drivers, win apps), when I realize that only the NTFS partition is visible. I start searching and find that some how my fat32 partition got semi-corrupted. The partition table seems fine, but it says FS corrupted. I got all of my data off of the vista partition but my 30gb of backups are MIA. I start to work through TestDisk, parted, fdisk, and Vista recovery console to put the FAT partition into a readable state but it doesn't work.

I'm not sure whether I've missed anything (probably have) but I need to get at the FAT partition. I'll try anything, I just can't download any big (>100mb) live cds (2gb limit from sympatico).

Also, shouldn't an internal IDE hd be hda? I'm on an E7205 (Granite Bay P4) chipset (single drive) and it is recognized as sda.

My live cd is Ubuntu 7.04.

Thanks,
Mike.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

IDE hardware now uses the scsi kernel drivers, so everything is now sdx....

Regardless of your partition table, it sounds like the filesystem is corrupt.  The best way to recover the data is to use data carving software.  Use foremost or photorec.  I would make an image of the partition before trying anything else to get the filesystem back into a usable state.

---

### Post by xzero1 on 2007-08-05
> Regardless of your partition table, it sounds like the filesystem is corrupt. The best way to recover the data is to use data carving software. Use foremost or photorec. I would make an image of the partition before trying anything else to get the filesystem back into a usable state.

The partition table holds the drives structure. It defines the type and extent of the filesystem(s)  (NTFS,DOS,EXT3) etc. The filesystem is dependent on the partition table not the other way around. If you cannot mount or see a partition the problem is likely with the partition table.

---

