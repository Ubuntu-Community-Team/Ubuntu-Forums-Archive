---
title: "Ubuntu 12.04 not working"
date: 2014-10-26
forum: General Help
---

### Post by notaki on 2014-10-26
hello every one..

my ubuntu not working anymore. i dont know the reson. It cant launch any more the menu, it cant open directories, it cant save. The only think i can do is run the terminal and Firefox. What can i do in order to save my files?
It can not see my usb flash so i cant take backup.
please help..

---

### Post by grahammechanical on 2014-10-26
Can you run a Ubuntu live session from a USB memory stick and save your files that way? Can you use the live session to create another partition, format it and copy your files over to the new partition?

Regards.

---

### Post by notaki on 2014-10-27
no i cant. i cant find the files. what can i do ?
partition did about an hour and it was stuck at the same time for long time.i am new in linux and i Know nothing just a few basic commands.

---

### Post by Bashing-om on 2014-10-27
notaki; Hi !

Let's see what we can do to help you find your files ( and perhaps salvage this install ?? ):
Boot the liveDVD to "try ubuntu" mode:
post back  - Between Code Tags - the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
The commands will relate to us the partitioning on the hard disk(s), and then we can mount the file systems and find your files - if they exist.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by notaki on 2015-02-15
i didnt fix it yet i left it because the work....
here is the code... is there a way to browse my files again ?

```

linuxlite@linuxlite-Lenovo:~$ sudo fdisk -lu
[sudo] password for linuxlite: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099e32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   310503423   155250688   83  Linux
/dev/sda2       310505470   312580095     1037313    5  Extended
/dev/sda5       310505472   312580095     1037312   82  Linux swap / Solaris

Disk /dev/sdb: 3965 MB, 3965190144 bytes
122 heads, 62 sectors/track, 1023 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
linuxlite@linuxlite-Lenovo:~$ sudo parted -l
Model: ATA WDC WD1600BEVS-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  159GB  159GB   primary   ext4            boot
 2      159GB   160GB  1062MB  extended
 5      159GB   160GB  1062MB  logical   linux-swap(v1)


Model: Generic- Multi-Card (scsi)
Disk /dev/sdb: 3965MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Error: /dev/zram0: unrecognised disk label   

```

---

### Post by Bashing-om on 2015-02-15
notaki; Hello once more ;

Well the partitions are there, bet the files are too.
To 'see' your files:
From the liveDVD; terminal commands:
```

sudo mkdir /mnt/look
sudo mount /dev/sda1 mnt/look
ls -al /mnt/look/
ls -al /mnt/look/home
ls -al /mnt/look/home/notaki

```

This is cause for a pause:
> 
Error: /dev/zram0: unrecognised disk label

zram0 from the liveUSB environmnet ? What is set up, how is the system attempting to access zram ?
Maybe a bad entry in the install's file system table ???
post back:
```

cat /mnt/look/etc/fstab

```

When all done look'n make sure to UNmount what you manually mounted:
```

sudo umount /mnt/look

```
else file system damage will result at some level.

Once you have 'seen' your files, one can copy them off either from terminal or the GUI file managr.

Better to fix this booting issue.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it is doable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by notaki on 2015-02-15
I installed ubuntu 2 years ago by LiveUsb. I was make update / upgrate in summer (command line)
after that appears the problem on folders. 
and i canot read my usb neither. generally , i can open nothing at all. neither menu .
I have not the liveusb now but i'll have it next days. all these commands are used only with live usb or i could now?

---

### Post by Bashing-om on 2015-02-15
notaki; Welllll ....

How did you provide the outputs of post # 5 ? .. You must have some means to access the system. I may be not understanding the issue here,
You can boot the install, but have no desktop (GUI ?) ??

If the file system of the install requires that we work on it, best done from a liveDVD(USB) .
If we are to copy files off from that installed system, got to have somewhere to copy them to  ( a USB stick/thumb drive  ?).

> 
I installed ubuntu 2 years ago by LiveUsb. 

What release are we working with ? 
We do not beat on dead horses. If that release is End_Of_Life -> install clean and fresh release 14.04 and be done with it.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by notaki on 2015-03-05
hello again,

i did everythink you said! I saved my files by the live Usb... I am going to install a new release.Thanks a lot to all!

---

### Post by Bashing-om on 2015-03-05
notaki; OK ;

Sounds like a plan to me.
Let us know how it goes and if you require additional guidance,

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

