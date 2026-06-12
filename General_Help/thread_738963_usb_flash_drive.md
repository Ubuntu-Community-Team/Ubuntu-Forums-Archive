---
title: "usb flash drive"
date: 2008-03-29
forum: General Help
---

### Post by hirohitosan on 2008-03-29
Hello to everyone.
My USB flash drive crashed. It cant be read. When inserting in my linux box it cant be read. When inserting in win box it says it must be formated. Is there any chance to recover the files on the flash drive? Any possibility to mount my USB drive? If I cannot save the files and I have to re-format the flash drive, what kind of file system should I choose? I want to read / write from many OS: linux, windows, mac ox. Any advice? Thanks a lot.

---

### Post by justleen on 2008-03-29
does ubuntu recognize the disk? as in, if you insert it, can you see it with ```
 fdisk -l 
```?

if so, you could try[ testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover files. Spinrite is ver good as well, but that is commercial.

---

### Post by alexpwalsh on 2008-03-29
I have a strange feeling your not going to get your files back... I had similar problems a while back with my actual hard drive. There are professional programs used by Law enforcement forensics to retrieve data from drives even after a format, so you could try to pirate a copy of some program like that. 
But I don't recommend it, cause you may get creamed for doing so...
You can try to force mount it, it may work. But its doubtful....
But to answer your second question(which file system to use) just go with FAT or FAT32, they're compatible with many(if not all) OS's. I know its not the best, but like I said, it works.
Best of luck....

---

### Post by strabes on 2008-03-29
Assuming your device is located at /dev/sdb1 (CHECK THIS FIRST with sudo fdisk -l), you can run this command to make a new fat32 filesystem on it:
```
sudo mkfs.vfat -n NAMEOFDISK /dev/sdb1
```

---

### Post by justleen on 2008-03-29
> **strabes said:**
> Assuming your device is located at /dev/sdb1 (CHECK THIS FIRST with sudo fdisk -l), you can run this command to make a new fat32 filesystem on it:
```
sudo mkfs.vfat -n NAMEOFDISK /dev/sdb1
```

that wouldnt get the data back?



and as far as forensic tools go, there are open source ones.. [Autospy/Sleuth]("http://www.sleuthkit.org/autopsy/") for examples.

---

### Post by hirohitosan on 2008-03-30
Thanks guys. 
:popcorn:

---

### Post by hirohitosan on 2008-03-30
well I don't know exactly what I did:
```
sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1761    13313128+   7  HPFS/NTFS
/dev/sda2            2534        4764    16866360    f  W95 Ext'd (LBA)
/dev/sda3            1762        1855      710608+  82  Linux swap / Solaris
/dev/sda4            1856        2533     5125680   83  Linux
/dev/sda5            3544        4764     9230728+   7  HPFS/NTFS
/dev/sda6            2534        3543     7630812   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2062 MB, 2062024704 bytes
64 heads, 62 sectors/track, 1014 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      196103      483782   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(196102, 51, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(483781, 40, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       42513      530423   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(42512, 30, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(530422, 52, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      471241      959151   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(471240, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(959150, 39, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      727239      727253       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(727238, 12, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(727252, 11, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Disk identifier: 0x6b736964

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   567332875  1110505095   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(567332874, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(1110505094, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   443394731   623053494   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(443394730, 0, 3)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(623053493, 0, 1)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   179663131   645784101   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(179663130, 0, 2)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(645784100, 0, 3)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?  1303039523  1303061302       32669+  bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(1303039522, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(96, 0, 7) logical=(1303061301, 0, 2)
Partition 4 does not end on cylinder boundary.

```

I don't understand everything but at least I discover something.
For example. I don't hnow what is /dev/sda2? My computer IBM T40, has a tool for reinstall WinXP and maybe the whole files for reinstallation are there. This partition was invisible for Partition Magic.

My flash drive has 2 partitions. When I mounted in a win box one partition is mounted like a floppy disk and the other like HDD drive. 

I tried ```
 sudo mkfs.vfat -n name /dev/sdb
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sdb' (use -I if wanted)
sudo mkfs.vfat -In name /dev/sdb
mkfs.vfat 2.11 (12 Mar 2005)

```
and I mounted the flash drive but the drive is empty. No files on it. Well at least I have an operational flash drive :)

If I try again 
```
sudo fdisk -l
Disk /dev/sdb: 2062 MB, 2062024704 bytes
64 heads, 62 sectors/track, 1014 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Disk identifier: 0x6b736964

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   567332875  1110505095   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(567332874, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(1110505094, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   443394731   623053494   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(443394730, 0, 3)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(623053493, 0, 1)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   179663131   645784101   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(179663130, 0, 2)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(645784100, 0, 3)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?  1303039523  1303061302       32669+  bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(1303039522, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(96, 0, 7) logical=(1303061301, 0, 2)
Partition 4 does not end on cylinder boundary.

```

I don't understand what are /dev/sdc1, /dev/sdc2, /dev/sdc3, /dev/sdc4?

and a final remark 
I launched GParted after that and I noticed that /dev/sdc is unallocated
and /dev/sdb is fat32 but has an exclamation mark on it. what does it means?

thanks and sorry for this long post

---

