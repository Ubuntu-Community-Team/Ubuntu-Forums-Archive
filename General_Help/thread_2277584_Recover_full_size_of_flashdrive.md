---
title: "Recover full size of flashdrive"
date: 2015-05-10
forum: General Help
---

### Post by masstumor29 on 2015-05-10
I&#7743; having a issue with my flash drive, I was making a live usb with ubootnetin and it kept screwing up on me. It wouldnt copy the iso contents to the drive but it would copy the boot files for the program. After a few failed attemps with that I used the live disk creator not knowing It wouldnt work with another debian iso. So after that failed I tried 

```
sudo dd if=/home/mass/Downloads/k/kali.iso of=/dev/sdb bs=16M
``` 

Only to fail with 

```
dd: error writing ‘/dev/sdb’: No space left on device
117+0 records in
116+0 records out
1961189376 bytes (2.0 GB) copied, 17.6896 s, 111 MB/s


```

My pen drive is an 8gb drive, before I started in gparted I formated the whole drive to fat32. It showed as 8gb fat32. After using dd I ca&#324;t get it to format right. it shows as 1.89gb in gparted now. When I plug it in it says on the icon when I hover over it 8.2gb volume but the only partion I can see is the 1.89gb.

Is there anyway I can fix my drive, I dont have any disks thats my only flash drive and my hdd is going bad. Really need this drive to install on the new sdd

```
mass@Mass:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099526

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   148178943    74088448   83  Linux
/dev/sda2       148180990   156301311     4060161    5  Extended
/dev/sda5       148180992   156301311     4060160   82  Linux swap / Solaris

Disk /dev/sdb: 1961 MB, 1961189376 bytes
179 heads, 32 sectors/track, 668 cylinders, total 3830448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34b1494d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     5854015     2926976   17  Hidden HPFS/NTFS
/dev/sdb2         5854016     5983103       64544    1  FAT12


```

---

### Post by Bucky Ball on 2015-05-10
Your problem was possibly that the USB stick wasn't empty in the first place. Best to wipe the drive by formatting it to FAT32, then you run Unetbootin or whatever it is you're using to create the install media.

Wipe that drive and reformat it to one empty FAT32 partition and try Unetbootin again.

---

### Post by masstumor29 on 2015-05-10
That&#347; the issue I cant wipe the whole drive. I been searching high and low to solve it. When I go to disk management and click on it, it is lable as PNY USB 2.0 FD (1100) 8.2 GB (8,166,703,104 bytes). It will let me format it there, when I format I use overwrite existing data with zeros. it&#314;l finish with no errors. When I go to gparted to format to fat32 I&#7743; shown unallocated 1.89gb. That&#347; all, not enough to make the bootable drive.

Edit:
I think I found the solution, trying to wipe it with shred it seems to be working if so it should allow me to fix the rest in gparted when complete.

```
mass@Mass:~$ sudo shred -v /dev/sdb1
shred: /dev/sdb1: pass 1/3 (random)...
shred: /dev/sdb1: pass 1/3 (random)...117MiB/7.7GiB 1%
shred: /dev/sdb1: pass 1/3 (random)...118MiB/7.7GiB 1%
shred: /dev/sdb1: pass 1/3 (random)...233MiB/7.7GiB 2%

```

---

### Post by sudodus on 2015-05-10
We don't know yet, how severe the damage is. If your pendrive is partially locked, it might be released by overwriting the whole system with zeros (at the level below file systems and partitions). So I suggest that you try mkusb

1. Wipe (overwrite) the first megabyte with mkusb, and after that use gparted to create a new partition table and after that a partition with a file system.

2. If that did not help, Wipe the whole device with mkusb, and after that use gparted to create a new partition table and after that a partition with a file system.

See this link [https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

['gridlock']("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426") - If a pendrive starts running slower, it might soon get 'gridlocked',  and wiping might relieve the situation by releasing good memory cells. 

- When old pendrives get slower  (typically reduce the writing speed to half), wiping the whole device  can recover the original (or near original) write speed. See [this link about pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297").

-o-

But if the internal system of the pendrive is damaged, there is not much you can do unless you get a special tool for that purpose from the manufacturer of the pendrive.

---

### Post by masstumor29 on 2015-05-10
Edit: Thank you!! After rebooting it allowed me to use mkusb to overwrite the first megabyte and fixed my drive. Everything is working as it should now.

---

### Post by Bucky Ball on 2015-05-10
Good news. Please mark the thread as solved to help others (see second link in my signature).

Enjoy! ;)

---

### Post by sudodus on 2015-05-10
Congratulations :KS

---

