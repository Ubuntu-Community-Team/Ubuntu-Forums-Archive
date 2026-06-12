---
title: "Grub error 16, 18"
date: 2007-11-25
forum: General Help
---

### Post by Willli on 2007-11-25
Hello!
I am a new user of Ubuntu 7.10 and I have some problems with Grub :( 
I receive next message errors when my computer starts "Grub Stage1.5 ReadError", "Grub Error 18", "Grub Error 16".The appearence of this errors is random. I restart my computer until the grub menu appears (sometimes I need at least 10 restarts).
I reinstalled grub. It works for 2 or 3 times, but after that it started again to show those errors. Then I reinstalled Ubuntu, but again after a  turn off the errors appeared again. 
I searched on Internet about this problem but the solutions did not work. 
I have a Western Digital hard disk (160 Gb) with the next partitions: 
1) a ntfs partition with WinXP 20 Gb
2) a swap partition 1 Gb
3) ext3 partition with Ubuntu 10Gb
4) fat32 partition 30 Gb
5) ntfs partition 90 Gb
The last three partition are made on an extended partition.
The number of ext3 partition is hda4 (I don't know why is this number).
For further information please let me a message and I will try to answer you as quickly I can.
P.S.1 I had installed Feisty Fawn and I didn't get any kind of error at grub.
P.S.2 Sorry for my poor English.

---

### Post by Sendervictorius on 2007-11-26
This link may help: [http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html)

1.5 Read Error = A disk read error happened while trying to read the stage2 or stage1.5
16 = internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB
18 = Selected cylinder exceeds maximum supported by BIOS. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general)

I suspect you have a hardware problem - since the grub errors are not consistent. Possibly your drive is failing, but perhaps a BIOS problem e.g. mistaken about the disk geometry, or motherboard failure). First thing I would check the obvious - that the IDE/SATA cable is not loose. Then I would back up any important data straight away!

Maybe others have some suggestions about what to do next to narrow down the problem.

---

### Post by jespdj on 2007-11-26
I also occasionally get GRUB error 16, 17 or 18 on my desktop PC. Most of the times I don't get those, just once in a while...

I found somewhere that this might be caused by certain CD/DVD drives. I have a Samsung SATA DVD writer and a Seagate SATA harddisk.

Things that might help:
- In the BIOS, set the harddisk as the first boot device (not the CD drive).
- Check if your SATA cables are seated correctly in their connectors.
- Plug the CD drive in a different SATA connector on the motherboard.
- Unplug the CD drive (just leave the harddisk connected) and check if GRUB still gives errors.

---

### Post by Willli on 2007-11-26
Thank you **jespdj** for your information, but my hard disk is on ATA 133 and it is my first booting device.
Saddly for me, the things are getting worse. Now I received the message: "No bootable device - insert boot disk and press any key" 
I try to repair the mbr from Windows XP repair console with fixmbr. After that I reinstalled Grub and it work just one time. Again the error appeared. I try to rerun Fixmbr from my Xp cd but it didn't work. So I run Fixboot. I expected to overwrite grub but at restart the menu of grub appeared.
Now I am in Ubuntu and I run fdisk -l and here is what I received:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dba2db9

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        2674      996030   82  Linux swap / Solaris
/dev/hda3            2675       19457   134809447+   f  W95 Ext'd (LBA)
/dev/hda5            2675        3824     9237312   83  Linux
/dev/hda6            3825        7649    30724281    b  W95 FAT32
/dev/hda7            7650       19457    94847728+   7  HPFS/NTFS


I hope that someone will tell me another solution otherwise I will try to do what **Sendervictorius** advised me.

---

### Post by Willli on 2007-11-29
The problem was solved. It was from my IDE cable. I changed it and all works fine.
Thanks a lot for help, especially **Sendervictorius** =D>

---

### Post by Sendervictorius on 2007-11-30
Glad I was of some help!  :)

---

