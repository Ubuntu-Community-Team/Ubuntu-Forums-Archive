---
title: "Ubuntu partition (turned to free space !) not showing anywhere ! Please help !"
date: 2017-09-21
forum: General Help
---

### Post by wankel-v on 2017-09-21
[SIZE=1][SIZE=2]Two days ago, I simply shut down when in windows but when turned on the next time errors were coming either unable to find disk to boot or disk read error.
I tried a Ubuntu live stick, but to my utter surprise both fdisk -lu & sfdisk -d gave the same output as below :-[/SIZE]
```
[SIZE=2]
ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda
Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1          2048    923647    921600   450M  7 HPFS/NTFS/exFAT
/dev/sda2  *    1161216 352759807 351598592 167.7G  7 HPFS/NTFS/exFAT[/SIZE]
```


[ATTACH=CONFIG]276796[/ATTACH]
[SIZE=2]The screenshot is of gparted and disk utility outputs where what used to be Ubuntu partition is showing up as free space !!!
I believe I'll be able to recover Windows but haven't tried yet because first I want to recover Ubuntu which is more important to me !
Please help ![/SIZE]

[/SIZE]

---

### Post by dragonfly41 on 2017-09-21
I'll throw in some ideas.
In your position these are the steps that I would follow:

(a) Get hold of another disk drive (larger capacity than your internal disk) which you can place in a disk drive container plugged in via USB port.   This might require you to go out and purchase some items.  But it can later be put to good use as your backup device after initial recovery exercise.   I recommend at least 500Gb since not only will you need to hold the cloned image but also (possibly) any data which has to be recovered from the cloned image.   On the other hand you might strike lucky and not need extra recovery space. 

(b) Using your LiveUSB clone your failed internal drive contents to your external USB drive.   You could use cloning packages such as clonezilla or R-Linux for this purpose.   They will  first need to be installed on your LiveUSB but if your LiveUSB has not been created as *persistent *device you might have problems when you shut down and restart LiveUSB. The reason for this cloning stage is to ensure that any recovery procedure does not do further damage.

(c) If you use dd or ddrescue to clone (as advised in different threads), do take great care not to screwup the command since you can easily destroy (wipe) the contents of original disk you are trying to recover.  That is why I do not suggest using dd or ddrescue. [https://wiki.gentoo.org/wiki/Ddrescue](https://wiki.gentoo.org/wiki/Ddrescue)   I suggest starting with R-Linux which is a GUI.

(d) Now with internal image safely cloned, install testdisk on your LiveUSB.

(e) Follow guide here ..

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

and make sure that your recovery operation is on the new *external* drive and not the original *internal* drive

(f) You could bypass the precautionary cloning stage and just apply testdisk to the original disk. 
But you have the risk that you lose everything if you screw up using testdisk.

...

You will find many threads by searching around .. read them to gain an understanding of the process (and risks) ..

[https://datarecovery.com/rd/how-to-clone-hard-disks-with-ddrescue/](https://datarecovery.com/rd/how-to-clone-hard-disks-with-ddrescue/)

[https://askubuntu.com/questions/24945/unallocated-space-with-important-data](https://askubuntu.com/questions/24945/unallocated-space-with-important-data)

[https://superuser.com/questions/710814/restore-data-on-unallocated-space](https://superuser.com/questions/710814/restore-data-on-unallocated-space)

---

### Post by oldfred on 2017-09-21
Did Windows do an update?
Since Windows 7 and thru most recent Windows 10 major updates in Windows conveniently "forget" to include one or more Linux partitions in the partition table when it rewrites partition table as part of update.

Many similar threads on above issue. Most were able to recover partition, but had to reinstall grub.

 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 
   [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by wankel-v on 2017-09-23
[ATTACH=CONFIG]276818[/ATTACH]
PFA as in the attached image parted was unable to find the partitions, was I supposed to do something else too besides that !
I am really feeling miserable after this & so many days have gone by ! I guess I should shift to Debian but am afraid from that too.

---

### Post by oldfred on 2017-09-23
It looks like you entered the existing partitions.
You want the start to be one or two sectors after the end of sda2 and end to be at end of drive which is shown as total size in header of parted listing of partitions.

---

### Post by wankel-v on 2017-09-25
Olfred, please look at the start and end sectors in the attached image again. I believe I did as you said. :)
Thanks

---

### Post by johndough2 on 2017-09-25
Hi

I wonder if clonezilla would give anymore clues?

There is certainly a gap in the number system.

Clonezilla, containing some other programs, can save and restore not only partitions, but also a whole disk.

It seems a Lo-Cost/No-Cost option.

---

### Post by dragonfly41 on 2017-09-25
clonezilla and R-Linux were suggested in post#2

---

### Post by oldfred on 2017-09-25
It looks like you entered the start & end of your existing partitions.
You want the missing partition which starts 1 or 2 sectors after the end of sda2 352759807 and ends near the end of the entire drive or 500118192.

---

### Post by efflandt on 2017-09-25
I have heard that Win10 updates sometimes make Linux partitions disappear, although, I have not had that problem (yet). I have Win7 on other computers or laptops with Ubuntu, but only have 1 laptop with Win10/Ubuntu 16.04 dual boot.

Try testdisk which is able to try to recover partitions or files, and includes photorec to specifically identify and recover multimedia files. The testdisk package is in the normal Ubuntu repositories. If you are going to try to recover files you should have another or external drive to write them to. You can read more about it at [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by wankel-v on 2017-09-28
Running testdisk on the original disk didn't offer any resolution. Should I still invest in Cloudzilla/ R-Linux ?

---

