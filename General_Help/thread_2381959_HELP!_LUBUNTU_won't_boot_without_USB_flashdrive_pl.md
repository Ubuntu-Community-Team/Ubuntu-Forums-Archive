---
title: "HELP! LUBUNTU won't boot without USB flashdrive plugged in"
date: 2018-01-07
forum: General Help
---

### Post by mushrambom on 2018-01-07
Hi, thats my first time using any kind of linux system, just trying to wake up an old computer and now facing this problem
I've searched on google already and looks like thats a recurrent problem but their solution didn't worked for me

This is what i get when used sudo fdisk-l

> Disk /dev/sda: 298,1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x59cb98e2

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  b W95 FAT32
/dev/sda2          206848 593043455 592836608 282,7G  b W95 FAT32
/dev/sda3       593043456 624928767  31885312  15,2G  7 HPFS/NTFS/exFAT
/dev/sda4       624928768 625139711    210944   103M  6 FAT16




Disk /dev/sdb: 7,5 GiB, 8054112256 bytes, 15730688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x637bea9d

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15728639 15726592  7,5G 83 Linux

I have tried to install it to sda already, using sudo grub-install /dev/sda and then updating... system tell me everything is installed ok but still won't boot without flashcard
also tried to use the boot repair program, still nothing 

can someone help me?

---

### Post by C.S.Cameron on 2018-01-07
Welcome to the Forums.

When installing to sda ensure the bootloader target is sda, (not sda1, sda2, etc).
This can be done when you get to partitioning using "Something else".
Sometimes it gets installed on the USB, then you need USB to boot.

---

### Post by oldfred on 2018-01-07
The only Linux partition is on your 7.5GB drive. Is that an internal drive or the flash drive.
And you do not have any Linux partitions on sda, the 298GB drive. 

And it looks like you have used all 4 primary partitions allowed with MBR partitioning on the sda drive, so no partition for Linux install.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

