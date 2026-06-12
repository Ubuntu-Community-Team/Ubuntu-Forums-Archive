---
title: "format fat32 flash drive as exfat"
date: 2013-07-31
forum: General Help
---

### Post by jon-zendatta on 2013-07-31
Hi all. Attempting to format usb stick.
```
[COLOR=#000000][FONT=Consolas]sudo add-apt-repository ppa:relan/exfat
[/FONT][/COLOR]
``````
sudo apt-get update

``````
sudo apt-get install fuse-exfat

```[COLOR=#000000][FONT=Consolas]sudo mkdir /media/exfat[/FONT][/COLOR]
```
sudo fdisk -l
```

/dev/sdb1              32     7821311     3910640    b  W95 FAT32

```
sudo mount -t exfat /dev/sdb1 /media/exfat

```
FUSE exfat 1.0.1
ERROR: exFAT file system is not found.

---

### Post by ian-weisser on 2013-07-31
The mount command mounts a filesystem. It does not reformat the filesystem.
You command is asking the system to mount a Fat32 filesystem as an exfat filesystem. The system, properly, scratches it's head and says "but...it's not an exfat filesystem"
And the system is right.

Do you want to reformat the flash drive from fat32 to exfat?
See [http://unix.stackexchange.com/questions/61209/create-and-format-exfat-partition-from-linux](http://unix.stackexchange.com/questions/61209/create-and-format-exfat-partition-from-linux)

Do you want to read from/write to an existing exfat filesystem?
See [http://stackoverflow.com/questions/6537878/how-to-mount-a-exfat-partition-in-ubuntu-11-04](http://stackoverflow.com/questions/6537878/how-to-mount-a-exfat-partition-in-ubuntu-11-04)

---

### Post by jon-zendatta on 2013-07-31
yes I'm wanting to reformat a usb stick to exfat. Your first link is broken i tried this

```
**mkfs -t vfat /dev/sdb1**
```

which isn't the answer

---

### Post by ian-weisser on 2013-07-31
How do you know it's not the answer? Did you try it? What happened?
Why did you specify vfat instead of exfat?
Did you remember to use sudo?

---

### Post by sudodus on 2013-07-31
Welcome to the Ubuntu Forums, jon-zendatta :-)

Exfat is a proprietary file system, that is not well supported in linux. If you have to format a partition with exfat, use Windows to do it.

And as hinted by ian-weisser, vfat is not the same as exfat. See this link

[https://en.wikipedia.org/wiki/File_Allocation_Table](https://en.wikipedia.org/wiki/File_Allocation_Table)

---

### Post by jon-zendatta on 2013-08-10
Maybe I need to use a windows box to do this. I tried:
```
 sudo mkfs -T exfat /dev/sdb1
```

No change
```
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              38     7839719     3919841    b  W95 FAT32

```

---

### Post by kurt18947 on 2013-08-10
I installed that ppa.  I created an exfat partition of a USB drive with windows.  I then installed the formatted drive in Ubuntu.  I was able to read and write data on both Windows & Ubuntu systems.  I did not try formatting but got the impression the ppa just enabled read/write, not formatting.

---

