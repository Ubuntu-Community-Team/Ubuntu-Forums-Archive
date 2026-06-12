---
title: "trying to get rid of sda"
date: 2014-10-30
forum: General Help
---

### Post by Peter_R._Larsen on 2014-10-30
ok

i have samsung m3 usb 3.0 external connected to my laptop it mark as sdb2 and i want it as only as sdb visible
how do i do it?
im trying get rid off sda on external harddisk with sdb

ive tried with 
sudo mount /dev/sdb2 /mnt
sudo mount --bind /dev /mnt/dev &&
sudo mount --bind /dev/pts /mnt/dev/pts &&
sudo mount --bind /proc /mnt/proc &&
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install
grub-install --recheck (no errors)
update-grub
exit &&
sudo umount /mnt/sys &&
sudo umount /mnt/proc &&
sudo umount /mnt/dev/pts &&
sudo umount /mnt/dev &&
sudo umount /mnt

originally it was with sdc, sda, sdb  and all internal harddisk os' and another external harddisk connected to my latop

sdb2 has Kali GNU/linux in it

just wanna get rid off sda

should there be any logs about it?
thanks

---

### Post by fantab on 2014-10-30
In linux /dev/sda means a Hard drive or SSD or USB-external. /dev/sda1, /dev/sda2 and so on, means partitions on /dev/sda.
/dev/sdb means a second HDD, and the partition on /dev/sdb will be represented as /dev/sdb1, /dev/sdb2 and so on.

I think you are confusing /dev/sdb1 with /dev/sda (/dev/sdb1 is a first partition on /dev/sdb while /dev/sda is another HDD altogether).

Post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by Peter_R._Larsen on 2014-10-30
> **fantab said:**
> In linux /dev/sda means a Hard drive or SSD or USB-external. /dev/sda1, /dev/sda2 and so on, means partitions on /dev/sda.
/dev/sdb means a second HDD, and the partition on /dev/sdb will be represented as /dev/sdb1, /dev/sdb2 and so on.

I think you are confusing /dev/sdb1 with /dev/sda (/dev/sdb1 is a first partition on /dev/sdb while /dev/sda is another HDD altogether).

Post the output of:
```
sudo parted -l
sudo fdisk -l
```

actually should have more specific

i choose boot with F9 which from external hardisk instead of internal, so sdb is there and there is sdas

---

### Post by fantab on 2014-10-31
Post the output of the commands I requested and tell us what exactly you want to get rid of after looking at the output.

---

### Post by Peter_R._Larsen on 2014-10-31
i havent exactly learn about those
you mean like this? "command > the output"

---

### Post by Peter_R._Larsen on 2014-10-31
> **fantab said:**
> Post the output of the commands I requested and tell us what exactly you want to get rid of after looking at the output.

[COLOR=#000000]i havent exactly learn about those[/COLOR]
[COLOR=#000000]you mean like this? "command > the output" and then uploaded?[/COLOR]

---

### Post by fantab on 2014-10-31
Boot into Ubuntu, open Terminal [ctrl+alt+T], run the commands one after another, copy and paste the output each command gives here.

Like this:

```
$ sudo parted -l
Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  21.5GB  21.5GB  primary   ext4            boot
 2      21.5GB  43.0GB  21.5GB  primary   ext4
 3      43.0GB  64.4GB  21.5GB  primary   ext4
 4      64.4GB  1000GB  936GB   extended
 5      64.4GB  996GB   931GB   logical   ext4
 6      996GB   1000GB  4298MB  logical   linux-swap(v1)
```

---

### Post by Peter_R._Larsen on 2014-10-31
> **fantab said:**
> Boot into Ubuntu, open Terminal [ctrl+alt+T], run the commands one after another, copy and paste the output each command gives here.

Like this:

```
$ sudo parted -l
Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  21.5GB  21.5GB  primary   ext4            boot
 2      21.5GB  43.0GB  21.5GB  primary   ext4
 3      43.0GB  64.4GB  21.5GB  primary   ext4
 4      64.4GB  1000GB  936GB   extended
 5      64.4GB  996GB   931GB   logical   ext4
 6      996GB   1000GB  4298MB  logical   linux-swap(v1)
```

ok, here there are, im booting kali gnu/linux external harddisk /dev/sdb, and tried sudo mount thingy to get rid of sdas

```
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  100GB  100GB   primary  ntfs            boot
 2      100GB   108GB  8000MB  primary  linux-swap(v1)
 3      108GB   500GB  392GB   primary  ext4


Model: Samsung M3 Portable (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.8kB  376GB   376GB   primary  ntfs
 2      376GB   999GB   623GB   primary  ext4
 3      999GB   1000GB  1049MB  primary  linux-swap(v1)  boot


```

---

### Post by yancek on 2014-10-31
From reading through your posts several times, I'm not sure exactly what you are trying to accomplish.  If you want to boot an operating system on the sdb drive (the 1TB) drive, then disconnect sda, the 500GB drive.  Otherwise it will show.

---

