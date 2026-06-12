---
title: "Trouble with grub, ERROR 15 - crucial - need help :("
date: 2007-08-22
forum: General Help
---

### Post by scubashoes on 2007-08-22
Hey all, I have a major problem I presume.  Anyways. . I was doing a dual boot with unbuntu 7.04 and windows xp on the same hard drive.  I decided I wanted to reinstall ubuntu on a smaller partition.  So within windows I used partition magic to delete the linux partitions and resize the main partition.  Doing so I amateurly restarted my computer to get a grub error 22.  So then I paniced and booted the ubuntu live cd, started gparted, resized and re-partitioned my hard drive. . reinstalled ubuntu. . . now I'm getting a grub error 15. 

SOOO..then I researched and tried loading xp with the xp install cd . . when I try to hit "r" to go into recovery console it doesn't detect that I have any hard disk drives installed.   Yet when I boot from ubuntu live cd, it is able to access all drives fine.  

I basically can't reformat the whole system cause I have crucial files I need to keep. . so any help is highly appreciated.  

(cliffenotes and summary)
HAD DUAL BOOT WITH XP
DELETED LINUX PARTITIONS
GOT GRUB ERROR 22
REINSTALLED UBUNTU 7.04
NOW GETTING GRUB ERROR 15
CAN'T BOOT FROM XP CD

Thanks in advance guys <3

---

### Post by merlinus on 2007-08-22
Try supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

-merlin

---

### Post by julian67 on 2007-08-22
error 15 means file not found, i.e the disks/partitions are seen but some important file is not seen by grub. 

error 22 means no such partition.

I can't say anything for sure because I don't know how your disk was partitioned, if you had Extended and Logical partitions, the sequence in which you made the partitions (and hence device names) and the order in which you installed XP and Ubuntu. I'd assume the error 22 is because the device names (i.e. sda1 or sda2 or hda1 etc) have changed and don't correspond to Windows C:\boot.ini or grub's menu.lst, or you may even have broken the partition table, which is seriously bad news. 

Before you do anything else you should use a live CD* and back up your valuable data to an external drive or to DVD/CD. 

Possibly you're going to end up reinstalling both systems. If you have plenty of external storage you should consider using clonezilla live in future to clone partitions or even the entire disk and to back up the partition table.  I'd suggest never using Partition Magic to modify any disk that has non-Microsoft filesystems, better options are Parted Magic and GParted, both Free software. 

If you have broken the partition table (i.e you can't do anything with the disk like boot XP installer, can't repair, can't modify the disk in any way) then use Partition Magic (or Parted Magic, as Partition Magic probably will refuse to perform any actions on the disk due to the errors it created :lolflag: ) to delete the entire disk, so you end up with a raw unpartitioned disk.  XP installer should now see it as a raw disk with no partitions and will be able to use it.  It's easiest to install XP first on the beginning of the first disk and then install your distro. 

Then get a copy of GParted-Clonezilla and a spare external drive for back ups and make it a habit to back up regularly.

* there are live CDs that load entirely into RAM and leave the CD/DVD drive free for you to use. Again, try Parted Magic.

---

