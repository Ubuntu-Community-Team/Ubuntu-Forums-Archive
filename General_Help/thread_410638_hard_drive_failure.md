---
title: "hard drive failure"
date: 2007-04-16
forum: General Help
---

### Post by StandardBlueCaboose on 2007-04-16
My hard drive containing the MBR for my computer has recently failed. I am wondering how to configure the MBR on another hard drive to boot grub and basically restore the performance I had before.

To clear up my hard drive situation:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/hda: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        7294    58556925    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    b  W95 FAT32
```

/dev/hda is failing, and sdd is an external drive. My plans are to copy hda to sdb and see if I can make anything of it.

If anybody can help, I'd appreciate it. Thanks.

---

### Post by dmizer on 2007-04-16
here's a little howto that might help you: [http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup) there's a link on how to restore your grub in there as well.

---

### Post by talcite on 2007-04-16
If you want to perform a sector for sector copy of your HDD, try using norton Ghost. I know it's windows, and not free =S. 

However, it's the only program I've got experience with. It boots off a CD, so you don't have to worry about putting it onto any HDD. You can copy everything over to the new HDD, with a full drive copy. It should do the boot sector and everything else as well. I don't remember what happens if your drives have different capacities though. You might have to make a second partition on the new drive =/.

---

