---
title: "Gutsy to recover xp 64 in raid 0"
date: 2008-04-21
forum: General Help
---

### Post by cloudeen on 2008-04-21
Im having problem booting up my win xp64, installed on a raid0 array(nvidia bios raid). the hdd is dying, i bought a new 500g hdd wanting to save all my data before it is too late.

i realise ubuntu gutsy might be able to help me in this case. While downloading gutsy 7.1 i try to serach around how i can read my ntfs in raid0 but it seems like i have to do it using command? im totally newbie with linux, is there a guide where i can get some info on how to do it? I have a floppy containing my 64bit raid driver, which i normally press F6 while the winxp64 cd is booting to feed it the driver. how can i feed the driver in ubuntu?

Thanks in advance.:)

---

### Post by cloudeen on 2008-04-22
after some reading, i tried to install dmraid and do the mounting. but
```
ubuntu@ubuntu:~$ sudo dmraid -tay
nvidia_bjadgfec: 0 625163520 striped 2 64 /dev/sda 0 /dev/sdb 0
nvidia_bjadgfec1: 0 81915372 linear /dev/mapper/nvidia_bjadgfec 63
nvidia_bjadgfec5: 0 543221847 linear /dev/mapper/nvidia_bjadgfec 81915498

```

```
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/mapper/nvidia_bjadgfec /media/raid
NTFS signature is missing.
Failed to mount '/dev/mapper/nvidia_bjadgfec': Invalid argument
The device '/dev/mapper/nvidia_bjadgfec' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

fdisk result as below:

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/mapper/nvidia_bjadgfec

Disk /dev/mapper/nvidia_bjadgfec: 320.0 GB, 320083722240 bytes
255 heads, 63 sectors/track, 38914 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_bjadgfec1   *           1        5099    40957686    7  HPFS/NTFS
/dev/mapper/nvidia_bjadgfec2            5100       38913   271610955    f  W95 Ext'd (LBA)
/dev/mapper/nvidia_bjadgfec5            5100       38913   271610923+   7  HPFS/NTFS
```

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/mapper/nvidia_bjadgfec1

Disk /dev/mapper/nvidia_bjadgfec1: 41.9 GB, 41940670464 bytes
255 heads, 63 sectors/track, 5098 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_bjadgfec1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/mapper/nvidia_bjadgfec1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/mapper/nvidia_bjadgfec1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/mapper/nvidia_bjadgfec1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```


```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/mapper/nvidia_bjadgfec5

Disk /dev/mapper/nvidia_bjadgfec5: 278.1 GB, 278129585664 bytes
255 heads, 63 sectors/track, 33813 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_bjadgfec5p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/mapper/nvidia_bjadgfec5p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/mapper/nvidia_bjadgfec5p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/mapper/nvidia_bjadgfec5p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

when i try to mount nvidia_bjadgfec1, ubuntu will freeze up.
Is my data in my raid0 hdd still recoverable?:(

---

