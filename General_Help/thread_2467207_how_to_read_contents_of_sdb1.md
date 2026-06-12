---
title: "how to read contents of sdb1"
date: 2021-09-18
forum: General Help
---

### Post by ford12 on 2021-09-18
Hi 
I have two harddrives installed and am trying to read the contents of my sdb1 harddrive. I have unbuntu installed on sda
This is what happens when I try to mount sdb1

[FONT=&quot]sudo mkdir /mnt/sdb1 (cannot create directory file exists)
sudo mount /dev/sdb1 /mnt/sdb1 (already mounted on /mnt/sdb1)

Since the drive is already mounted, I then type   ls and press enter (to display the directories on the sdb1 drive)
but this is the directory list for what is on the first drive  - bin, boot, cdrom, dev, dir1, etc, hdd, home, home.orig, lib, lib32, lib64..............................


 Thanks

 [/FONT]

---

### Post by Bashing-om on 2021-09-18
ford12; Hello - Welcome to the Forum

As you say:
> 
Since the drive is already mounted, I then type ls and press enter 

then I do expect "ls" to direct to sda as that, I think, is your PWD (present working directory).

Explicitly -
what results with sdb1 mounted from  terminal commands:
```

sudo fdisk -lu
ls -al /mnt/sdb1

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

whereas I can also anticipate that access to the file system on sdb1 will have to be changed to "you".

[INDENT]stupid computer
[INDENT][INDENT]can not read minds
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2021-09-19
Is sdb1 the label of this second drive? Normally sdb1 would indicate the first partition on sdb. I assume that sdb1 is the label. You have mounted the drive in /mnt/.

Open the terminal and change directory like this

```
cd /mnt/sdb1
```

now run the ls command.

For information purposes: when we access a partition using the file manager it gets mounted at /media/. 

Regards

---

