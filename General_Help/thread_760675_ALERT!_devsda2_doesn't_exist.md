---
title: "ALERT! /dev/sda2 doesn't exist"
date: 2008-04-20
forum: General Help
---

### Post by fadey on 2008-04-20
Hi, everyone

I've upgraded to hardy rc (2.6.24-16-i386 kernel). When booting the system, I'm getting a message:
ALERT! /dev/sda2 does not exist

After that I'm being dropped to initramfs shell.

I guess I'm missing something in my initramfs image. These are fs-related modules that are in the image:
cat /proc/modules
...
md_mod
dm_mod
ext3
ata_generic
ata_piix
libata
scsi_mod
...

Is that enough to make an IDE drive work? I have a SIS 5513 IDE controller.
Thanks in advance

---

### Post by Dmole on 2008-04-20
not sure I get the problem but 
what is /dev/sda2 used for?
is it / or some other drive you could boot without?
you could try a live cd and look at the partitions on your drives
( normaly one or more of /dev/sda /dev/sdb /dev/hda /dev/hdb )
what dose your fstab say?

---

### Post by confused57 on 2008-04-20
> **fadey said:**
> Hi, everyone

I've upgraded to hardy rc (2.6.24-16-i386 kernel). When booting the system, I'm getting a message:
ALERT! /dev/sda2 does not exist

After that I'm being dropped to initramfs shell.

I guess I'm missing something in my initramfs image. These are fs-related modules that are in the image:
cat /proc/modules
...
md_mod
dm_mod
ext3
ata_generic
ata_piix
libata
scsi_mod
...

Is that enough to make an IDE drive work? I have a SIS 5513 IDE controller.
Thanks in advance
You can use the live cd(Hardy) to determine how your partitions are designated:
```
sudo fdisk -l
```
-l is a small "L"

Then you can mount your root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/xxx /media/ubuntu
```
It would help if you could post the output of:
```
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/etc/fstab
```

and the ouput of:
```
blkid
```

---

