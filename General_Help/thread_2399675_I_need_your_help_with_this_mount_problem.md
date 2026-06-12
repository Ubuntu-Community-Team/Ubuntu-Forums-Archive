---
title: "I need your help with this mount problem"
date: 2018-08-28
forum: General Help
---

### Post by carmatope on 2018-08-28
```
There was an error accessing "2.7 TiB Hard Drive",
the system responded:
The requested operation has failed: 
Error mounting /dev/sdd2 at /media/cm/780a98da-4ccf-46f8-a53b-f0f86181df7d: 
Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid"
"/dev/sdd2" "/media/cm/780a98da-4ccf-46f8-a53b-f0f86181df7d"
'exited with non-zero exit status 32: 
mount: wrong fs type, bad option, bad superblock on /dev/sdd2,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail or so.
```


As you can see reinstalling it's a major loss of information.


Things you must know:
It was a guided installation
Don't has partition /home


When I've tried to repair the installation from a live usb 
I've noticed there is an option to install without formatting.


My question is:
Can I reinstall without losing it all or there is another solution? :confused:

---

### Post by Bashing-om on 2018-08-28
carmatope; Hello - Welcome to the forum

Not much to work with here ; Boot up a liveUSB and show us:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
and we see what the story is.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by carmatope on 2018-08-29
> **Bashing-om said:**
> carmatope; Hello - Welcome to the forum

Not much to work with here ; Boot up a liveUSB and show us:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
and we see what the story is.[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


**lubuntu@lubuntu:~$ sudo fdisk -lu**
```
Disk /dev/loop0: 866,8 MiB, 908898304 bytes, 1775192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 2,7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6292731D-5E8F-4B56-A167-A733D10E7A61

Device          Start        End    Sectors  Size Type
/dev/sda1        2048       4095       2048    1M Linux filesystem
/dev/sda2        4096 5843847167 5843843072  2,7T Linux filesystem
/dev/sda3  5843847168 5860532223   16685056    8G Linux swap


Disk /dev/sdb: 7,2 GiB, 7736072192 bytes, 15109516 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000598cc

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15109515 15107468  7,2G  c W95 FAT32 (LBA)


Disk /dev/zram0: 661,2 MiB, 693305344 bytes, 169264 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 661,2 MiB, 693305344 bytes, 169264 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram2: 661,2 MiB, 693305344 bytes, 169264 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram3: 661,2 MiB, 693305344 bytes, 169264 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram4: 661,2 MiB, 693305344 bytes, 169264 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram5: 661,2 MiB, 693305344 bytes, 169264 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

**lubuntu@lubuntu:~$ sudo parted -l**
```
Model: ATA WDC WD30PURX-64P (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB
 2      2097kB  2992GB  2992GB  ext4
 3      2992GB  3001GB  8543MB  linux-swap(v1)


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdb: 7736MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7736MB  7735MB  primary  fat32        boot, lba


Model: Unknown (unknown)
Disk /dev/zram5: 693MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0,00B  693MB  693MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram3: 693MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0,00B  693MB  693MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram1: 693MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0,00B  693MB  693MB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: TSSTcorp CDDVDW SH-222AB (scsi)                                    
Disk /dev/sr0: 644MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

Model: Unknown (unknown)
Disk /dev/zram4: 693MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0,00B  693MB  693MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram2: 693MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0,00B  693MB  693MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram0: 693MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0,00B  693MB  693MB  linux-swap(v1)
```


**lubuntu@lubuntu:~$ sudo blkid**
```
/dev/sda2: UUID="780a98da-4ccf-46f8-a53b-f0f86181df7d" TYPE="ext4" PARTUUID="c7a88475-dee1-4803-a357-6e0a6cb034fc"
/dev/sdb1: LABEL="LUBUNTU 16_" UUID="4A08-18C8" TYPE="vfat" PARTUUID="000598cc-01"
/dev/sda3: UUID="6a6fcba4-eef4-4607-bb8f-1e351dd93b9b" TYPE="swap" PARTUUID="6337e058-b54b-43ef-95d4-0b442becf173"
/dev/loop0: TYPE="squashfs"
/dev/zram0: UUID="45a21b42-91c8-4466-8843-464c1589c880" TYPE="swap"
/dev/zram1: UUID="227664c9-8224-49b2-a602-e36dc54a5d06" TYPE="swap"
/dev/zram2: UUID="74b482d1-83bb-4695-80f6-04a9ca595aaa" TYPE="swap"
/dev/zram3: UUID="1c52bed4-ddcb-4e87-a0be-c24345a6314d" TYPE="swap"
/dev/zram4: UUID="e009eea0-b26a-4d19-b4e6-817c50fe0bc4" TYPE="swap"
/dev/zram5: UUID="c9f6c450-0f03-4ddf-919b-c14611be09cf" TYPE="swap"
/dev/sda1: PARTUUID="c2ba6fe9-0734-4a6b-97b3-d6fac9d84ec7"
```


**Hope this could help, thanks :p**

---

### Post by SeijiSensei on 2018-08-29
> Error mounting /dev/sdd2 at /media/cm/780a98da-4ccf-46f8-a53b-f0f86181df7d: 

There is no /dev/sdd.  I only see /dev/sda, with three partitions, and /dev/sdb with one.

---

### Post by carmatope on 2018-08-29
> **SeijiSensei said:**
> There is no /dev/sdd.  I only see /dev/sda, with three partitions, and /dev/sdb with one.

So what's the solution? I can't access my hard drive at all.

---

### Post by Bashing-om on 2018-08-29
carmatope; well,

We now know that the ubuntu install is on sda2; let's take a look and see what is set to mount.
From the liveUSB;
```

sudo mkdir /mnt/look/
sudo mount /dev/sda2 /mnt/look/

```
and now show us the output of terminal command:
```

cat /mnt/look/etc/fstab

```
Once done, back out of the mount operation to preclude file system corruption. You mounted it and the system does expect  you to UN-mount.
```

sudo umount  /dev/sda2

```

[INDENT][INDENT]see where we stand in that process
[/INDENT][/INDENT]

---

