---
title: "How can I mount this HD?"
date: 2012-12-22
forum: General Help
---

### Post by sodaa on 2012-12-22
I'm trying to mount a 1TB HD that was appearing fine yesterday before I reinstalled ubuntu 12.04. I used to have a dual boot windows 7/ubuntu 12.04, and my 1TB drive would show up fine from either OS. Today, I wiped my main drive in order to use it all for Ubuntu 12.04, i.e., remove windows 7, and now I'm trying to mount the 1TB drive on the new installation without much success.

Here is the fdisk output for the device I'm trying to mount:

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f25ce66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1953523119   976761528+  42  SFS
```


I tried running sudo mount /dev/sdb /media, but I get: mount: you must specify the filesystem type

If I try to run sudo mount -t sfs /dev/sdb /media, I get: mount: unkown filesystem type 'sfs'

I also tried mounting as ntfs, ntfs-3g, and a few other types, but of course this doesn't work either.

How can I mount this HD?

---

### Post by Bashing-om on 2012-12-22
sodaa; Hi !

Never seen a "sfs" file system, so a default mounting possibly no will workie.
But try this:
Make a mount point to attach the drive to the file system thus:
```
sudo mkdir /mnt/backup
```now mount the drive thus:
```
sudo mount /dev/sdb1 /mnt/backup
```See now if you can access the files on the drive and play around, When done remember will have to manually (un)mount the drive to keep the file system happy:
```
sudo umount /mnt/backup
``` (yeah, u m o u n t is correct.)..

If the manual mounting is doable, will work on getting fstab to work.
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by sodaa on 2012-12-22
Thanks, but no luck with the mount:

```
$ sudo mount /dev/sdb1 /mnt/backup
mount: you must specify the filesystem type
```

Yah, I haven't encountered sfs before either. I was thinking the first time I went to install ubuntu I forgot to set where to place the boot loader; might it have been /dev/sdb by default and the bootloader is being interfering with the drive type/recognition somehow?

---

### Post by steeldriver on 2012-12-22
a bit of googling suggests it might actually be a Windows dynamic disk (LDM) - and the SFS designation is due to fdisk misinterpreting the 0x42 partition type as an SFS filesystem 

[http://ubuntuforums.org/showthread.php?t=1839373](http://ubuntuforums.org/showthread.php?t=1839373)

---

### Post by Bashing-om on 2012-12-22
sodaa;
Houston, we have a problem.   (maybe)... I look at man mount -> supported file systems : and sfs is NOT listed. ---how then is fdisk able to give it an ID ??---

Next item, grub installation:
```
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
```will tell you where grub is installed to.

If it returns "sdb" I am really going to be scratching my head!
[INDENT][INDENT]I still learning <== BDQ

[/INDENT][/INDENT]

---

### Post by fdrake on 2012-12-22
> **Bashing-om said:**
> sodaa;
Houston, we have a problem.   (maybe)... I look at man mount -> supported file systems : and sfs is NOT listed. ---how then is fdisk able to give it an ID ??
disk-id is not uuid. disk-id is for the disk , uuid is for the partition. mount does not mount disk but partitions..

---

### Post by sodaa on 2012-12-22
Grub is on /dev/sda, I was just thinking, I was having problems installing before and I noticed that the default was set to /dev/sdb for boot loader, I may have left it and run an install a few times before I eventually got everything working and set up the boot loader on /dev/sda. Wasn't sure if this might have done something is all.


> $ sudo file -s /dev/sda
/dev/sda: x86 boot sector; partition 1: ID=0x83, active, starthead 32, startsector 2048, 453122048 sectors; partition 2: ID=0x5, starthead 254, startsector 453126142, 15622146 sectors, code offset 0x63
$ sudo file -s /dev/sdb
/dev/sdb: x86 boot sector; partition 1: ID=0x42, active, starthead 1, startsector 63, 1953523057 sectors, code offset 0x63, OEM-ID "      &#1084;", Bytes/sector 190, sectors/cluster 124, reserved sectors 191, FATs 6, root entries 185, sectors 64514 (volumes <=32 MB) , Media descriptor 0xf3, sectors/FAT 20644, heads 6, hidden sectors 309755, sectors 2147991229 (volumes > 32 MB) , physical drive 0x7e, dos < 4.0 BootSector (0x0)

---

### Post by Bashing-om on 2012-12-23
OK, let's see what we are working with (dynamic partitioning ??)

Give the results of terminal codes:
```
ls /dev/sdb*
ls /dev/mapper/*
```[INDENT]where there is a will there is a way ==> BDQ

[/INDENT]

---

### Post by sodaa on 2012-12-23
```
$ ls /dev/sdb*
/dev/sdb  /dev/sdb1
$ ls /dev/mapper
/dev/mapper/control
```

---

### Post by rnerwein on 2012-12-23
> **sodaa said:**
> I'm trying to mount a 1TB HD that was appearing fine yesterday before I reinstalled ubuntu 12.04. I used to have a dual boot windows 7/ubuntu 12.04, and my 1TB drive would show up fine from either OS. Today, I wiped my main drive in order to use it all for Ubuntu 12.04, i.e., remove windows 7, and now I'm trying to mount the 1TB drive on the new installation without much success.

Here is the fdisk output for the device I'm trying to mount:

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f25ce66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1953523119   976761528+  42  SFS
```
I tried running sudo mount /dev/sdb /media, but I get: mount: you must specify the filesystem type

If I try to run sudo mount -t sfs /dev/sdb /media, I get: mount: unkown filesystem type 'sfs'

I also tried mounting as ntfs, ntfs-3g, and a few other types, but of course this doesn't work either.

How can I mount this HD?
hi
i never used it - but see:
[http://manpages.ubuntu.com/manpages/hardy/man7/sfs.7.html](http://manpages.ubuntu.com/manpages/hardy/man7/sfs.7.html)
cheers

---

### Post by Bashing-om on 2012-12-23
sodaa; and all ->

I do not know what to make of this. I had expected the output of "/dev/mapper" to indicate dynamic partitioning... humm, - I stand in need of education. On my 3 hard disk 'buntu installs -. out put from "ls /dev/mapper" is a mere " "control"- // does sodaa's output of "/dev/mapper/control" and no other files still indicate a dynamic partitioning scheme ? If those results show conventional partitioning, how come fdisk shows a "sfs" file system ?

Are we to the point of installing that disk on a windows box and looking at the disk from a windows perspective ?
[INDENT][INDENT]I find myself lacking <== BDQ

[/INDENT][/INDENT]

---

