---
title: "Have to use fsck.ext4 after every boot to be able to mount a disk"
date: 2021-09-07
forum: General Help
---

### Post by halluz on 2021-09-07
I think i have deleted the first partition of some disks in gparted few weeks ago because i thought it was some old operation system stuff i dont need anymore. Well there i am proven wrong, silly me.

Have i deleted the partition table? Is the partition table the first partition?

How to fix this?

---

### Post by Bashing-om on 2021-09-07
halluz; Well -

The fact that you can boot at all rules out that the partition table *OR* your boot partition was deleted :D

Show us what we are working with:
```

sudo parted -l
sudo blkid
cat /etc/fstab

```

Before we go checking drive health and file system integrity.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by halluz on 2021-09-08
```
sudo parted -l
Model: ATA ST14000NM001G-2K (scsi)
Disk /dev/sda: 14,0TB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0,00B  14,0TB  14,0TB  ext4




Model: ATA ST14000NM001G-2K (scsi)
Disk /dev/sdb: 14,0TB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                          Flags
 1      17,4kB  16,8MB  16,8MB               Microsoft reserved partition  msftres




Model: ATA ST8000DM004-2CX1 (scsi)
Disk /dev/sdc: 8002GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start  End  Size  File system  Name  Flags




Model: ATA Crucial_CT120M50 (scsi)
Disk /dev/sdd: 120GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   120GB  119GB  ext4




Model: ATA ST8000DM004-2CX1 (scsi)
Disk /dev/sde: 8002GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0,00B  8002GB  8002GB  ext4




Model: Samsung SSD 970 EVO Plus 1TB (nvme)
Disk /dev/nvme0n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start  End     Size    File system  Name                          Flags
 1      556MB  661MB   105MB   fat32        EFI system partition          boot, esp
 2      661MB  677MB   16,8MB               Microsoft reserved partition  msftres
 3      677MB  1000GB  1000GB  ntfs         Basic data partition          msftdata



```

```
sudo blkid
/dev/sdd2: UUID="9ac87e22-e276-47f3-94ec-6f1afd3ac2d3" TYPE="ext4" PARTUUID="bbdfad59-d061-49d3-8be8-f6472e009171"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/nvme0n1p1: UUID="06A2-CBA0" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="f17fec32-119e-4243-b046-b5ccccb9cd5d"
/dev/nvme0n1p2: PARTLABEL="Microsoft reserved partition" PARTUUID="78578853-9c81-4ce3-b6e3-9c90e8b049b0"
/dev/nvme0n1p3: UUID="4242E47742E470D9" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="41000acd-2b2b-4d10-9a75-0d6f39e1b561"
/dev/sda: LABEL="hdd8" UUID="31d65428-3d9d-4d0c-aaed-1cac41690423" TYPE="ext4"
/dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="b19279ca-dddb-41cd-8af8-2f2ed661b8d9"
/dev/sde: LABEL="hdd14" UUID="49dfe30f-c85c-4db7-acf4-c4f965b4c70e" TYPE="ext4"
/dev/sdc: PTUUID="296ab478-d5b3-4e6e-8ec6-1330dd7c6ad4" PTTYPE="gpt"
/dev/sdd1: UUID="5BF5-5A6F" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="fbd687c7-ec7f-4cd7-b1ec-c57a310a4516"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=9ac87e22-e276-47f3-94ec-6f1afd3ac2d3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/mmcblk0p1 during installation
#UUID=BEF6-5E85  /boot/efi       vfat    umask=0077      0       1
#/swapfile                                 none            swap    sw              0       0
#UUID=5BF5-5A6F  /boot/efi       vfat    defaults      0       1
UUID=b9827505-d5da-47c7-ade8-32065cf664e2 /mnt/hdd1 ext4 rw,relatime 0 0
UUID=c7e17c20-8b03-4808-8688-f52afe290949 /mnt/hdd2 ext4 rw,relatime 0 0
UUID=1a3b96be-1637-4205-b62e-e1d0f6696af4 /mnt/hdd3 ext4 rw,relatime 0 0
UUID=1e585d1d-38f7-4804-9e58-2af8ee716c31 /mnt/hdd4 ext4 rw,relatime 0 0
UUID=120f85c5-1173-4f8e-b005-929478069f74 /mnt/hdd5 ext4 rw,relatime 0 0
UUID=ac61dbf0-671c-42ad-a250-14cc107257df /mnt/hdd6 ext4 rw,relatime 0 0
UUID=447066e2-5f5b-46ec-adfa-c8dd587930ef /mnt/hdd7 ext4 rw,relatime 0 0
UUID=31d65428-3d9d-4d0c-aaed-1cac41690423 /mnt/hdd8 ext4 rw,relatime 0 0
UUID=dd0dd2ed-c56a-4b24-9061-ca67ba71c2d3 /mnt/hdd9 ext4 rw,relatime 0 0
UUID=d0723af3-b4ed-4259-af47-9cc0bb422904 /mnt/hdd10 ext4 rw,relatime 0 0
UUID=d37c0d68-dc33-460d-bae9-c538b87178fa /mnt/hdd11 ext4 rw,relatime 0 0
UUID=ccbda4c2-289b-474c-b5ba-8f9b30fe19e8 /mnt/hdd12 ext4 rw,relatime 0 0
UUID=17a975e7-c074-4511-af28-5a22c9ad4e06 /mnt/hdd13 ext4 rw,relatime 0 0
UUID=49dfe30f-c85c-4db7-acf4-c4f965b4c70e /mnt/hdd14 ext4 rw,relatime 0 0
UUID=ef1ee8db-86ac-4007-893c-5b1972ea1526 /mnt/hdd15 ext4 rw,relatime 0 0
UUID=7ddc63ef-2f07-4acf-a2f9-8c61df16e2d5 /mnt/ssd1 xfs rw,relatime,attr2,discard,inode64,logbufs=8,logbsize=32k,sunit=256,swidth=256,noquota 0 0
UUID=afa60865-9c4a-4f26-a7f1-b7485a27972f /mnt/ssd2 xfs rw,relatime,attr2,discard,inode64,logbufs=8,logbsize=32k,sunit=256,swidth=256,noquota 0 0
UUID=90c19595-d1e0-4898-b9ab-62514c9e3ddb /mnt/ssd3 xfs rw,relatime,attr2,discard,inode64,logbufs=8,logbsize=32k,noquota 0 0
UUID=71f39d5d-1fe8-4fbd-b117-95f841c52748 /mnt/ssd4 xfs rw,relatime,attr2,discard,inode64,logbufs=8,logbsize=32k,noquota 0 0
UUID=af8fbf8b-4f46-4d15-bd13-5d76f543e482 /mnt/ssd5 xfs rw,relatime,attr2,discard,inode64,logbufs=8,logbsize=32k,noquota 0 0

```


So sda and sde are mounting at start like they should, but sdb and sdc are saying "free space" in gnome and i need to do this for both of them:


```
sudo fsck.ext4 -v /dev/sdc
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
hdd6: recovering journal
Pass 1: Checking inodes, blocks, and sizes
...
hdd6: ***** FILE SYSTEM WAS MODIFIED *****


          84 inodes used (0.00%, out of 1907744)
           0 non-contiguous files (0.0%)
           1 non-contiguous directory (1.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 2/74
  1940268257 blocks used (99.32%, out of 1953498368)
           0 bad blocks
          74 large files


          73 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
          75 files

```

After that i just have to mount it manually and its working.
I was using Windows with wsl to use these drives the last weeks and of course same problem there. Maybe wsl corrupted smth?

---

### Post by Bashing-om on 2021-09-09
halluz; Ouch -

The complexity here boggles my little mind - messed up on so many fronts.

However, I think we want to start here:
```

ls -alh /dev/disk/by-uuid

```
for what the kernel maps the UUIDs to the devices.
Once you know what devices you want mounted at boot ----
Then edit /etc/fstab to what the kernel indicates for the hardware,

-all in that process-

---

### Post by halluz on 2021-09-10
The problem is that some drives are not detected like they should.
They are recognized as free space or whatever until I start fsck.ext4.

The uuid s are already correctly in the fstab and it actually did work some weeks ago. 

These unmountable drives either don't have uuids or only ptuuid until I start Fsck.ext4 for these drives. 
After that they are mountable and recognized correctly by the OS

---

### Post by Bashing-om on 2021-09-10
halluz; Yuk

Nope -
> 
The uuid s are already correctly in the fstab 


I suggest that you compare the listed UUID's in the /etc/fstab file to what "blkid" reports for the known UUID's - does not compute.
I would expect any UUID in the /etc/fstab file to also exist in other system listings.
Maybe update what "blkid" reports ?
```

sudo blkid -c /dev/null -o list

```
The switch "-c /dev/null" ensures the command is not using any cached values and polls all of your hardware directly. The "-o list" switch is an option to order the output for easier reading.
see our fine manual too:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

To see what the system thinks of the fstab file, run:
```

sudo mount -a

```

[INDENT]fstab rules automounting
[/INDENT]

---

### Post by halluz on 2021-09-12
> **Bashing-om said:**
> halluz; Yuk

Nope -


I suggest that you compare the listed UUID's in the /etc/fstab file to what "blkid" reports for the known UUID's - does not compute.
I would expect any UUID in the /etc/fstab file to also exist in other system listings.
Maybe update what "blkid" reports ?
```

sudo blkid -c /dev/null -o list

```
The switch "-c /dev/null" ensures the command is not using any cached values and polls all of your hardware directly. The "-o list" switch is an option to order the output for easier reading.
see our fine manual too:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

To see what the system thinks of the fstab file, run:
```

sudo mount -a

```[INDENT]fstab rules automounting
[/INDENT]

uuid only appears in system listings after "fsck.ext4" or "e2fsck". The uuid appearing after "fsck.ext4" is inside fstab and after "sudo mount -a" it mounts successfully. But next boot i have to do "fsck.ext4" or "e2fsck" and mount again.

---

### Post by Bashing-om on 2021-09-12
halluz; Yukkie 

on me --
I have no idea as to what could be overwriting the /etc/fstab file .

[INDENT][INDENT]a know-it-all
[INDENT][INDENT]I am not
[/INDENT][/INDENT]l[/INDENT][/INDENT]

---

