---
title: "Trying to resize ext4 Ubuntu partition using gparted"
date: 2016-11-03
forum: General Help
---

### Post by PlagueGiver on 2016-11-03
I'm trying to remove 50 gibs from my Ubuntu partition to create an ntfs partition. I used a gparted live dvd to do so and it gave me an error.

---

### Post by Bashing-om on 2016-11-03
PlagueGiver; Hello;

Way to vague to offer an opinion. Can you provide a screenshot of GParted in the re-size process ? 
Please advise which partition(s) you are operating on.

[INDENT][INDENT]ain't nothing  but a thing
[/INDENT][/INDENT]

---

### Post by PlagueGiver on 2016-11-03
Here's a screenshot
[http://imgur.com/a/KelKd](http://imgur.com/a/KelKd)

---

### Post by Bashing-om on 2016-11-03
PlagueGiver; Ho Kay;

And, have you followed the given advise :
From the liveDVD(USB) ran terminal command:
```

sudo e2fsck -fy /dev/sda1

```
in an attempt to fix the partition table ?

If there continues a issue, please show the output of the 'e2fsck' command - between code tags.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT][INDENT]so far
[INDENT][INDENT][INDENT]bent, but not broken
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by PlagueGiver on 2016-11-03
Tried it, not working:
```

e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 661890/38690816 files (0.6% non-contiguous), 86693476/154733568 blocks


```

---

### Post by Bashing-om on 2016-11-03
PlagueGiver; Yeah !

Looks good to me .

Does terminal command:
```

sudo parted -l

```
show the newly created NTFS partition ?

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by PlagueGiver on 2016-11-03
No, it hasn't been created yet since the gparted resize still isn't working :(:confused:
It still gives me the same error and tells me to run the same command!

---

### Post by Bashing-om on 2016-11-03
PlagueGiver'; Yuk ...

OK .. show us :
```

sudo fdisk -lu
sudo blkid

```
we see here what the state is, and if the numbers add up .

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by PlagueGiver on 2016-11-03
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1237870591   618934272   83  Linux
/dev/sda2      1237872638  1250263039     6195201    5  Extended
/dev/sda5      1237872640  1250263039     6195200   82  Linux swap / Solaris


```
And
```

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660" 
/dev/loop1: TYPE="squashfs" 
/dev/sda1: UUID="741310ec-8ba9-4012-9fe0-35ded7c79812" TYPE="ext4" 
/dev/sda5: UUID="53b81d68-4766-44be-b86e-856d7f5cb1e9" TYPE="swap" 
/dev/sr0: LABEL="LXFDVD187" TYPE="iso9660" 

```

---

### Post by Bashing-om on 2016-11-03
PlagueGiver; Well,

The numbers are acceptable, I do not know now what to advise .
Maybe show a screenshot of what GParted shows for the partitions of the sda drive ?

[INDENT][INDENT][INDENT]ouch
[INDENT][INDENT][INDENT]I hate when this happens
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by PlagueGiver on 2016-11-03
[http://imgur.com/a/K46Kg](http://imgur.com/a/K46Kg)

---

### Post by PlagueGiver on 2016-11-03
Here you go!

---

### Post by PlagueGiver on 2016-11-03
[http://imgur.com/a/K46Kg](http://imgur.com/a/K46Kg) this is the gparted screenshot

---

### Post by PlagueGiver on 2016-11-03
Sorry about all the reposts, my internet is acting up. :oops:

---

### Post by deadflowr on 2016-11-03
> **PlagueGiver said:**
> Sorry about all the reposts, my internet is acting up.

It's not you, it's the forums.
I'm trying to remove all the image post duplicates.

But in the mean time, you need to disable swap.
right click on the swap partition and select swap off.
then try resizing.

---

### Post by Bashing-om on 2016-11-03
PlagueGiver; Well, well ....

GParted seems happy with the present state of the affair .

maybe, just maybe
select the swap partition and "swap off " .
Now see if GParted will allow you to shrink sda1 .
Be aware that it is possible that the system will now assign a new UUID to sda1 . In that event you will have to edit the installed /etc/fstab file to reflect the change, and as well propagate the change to grub .



cheers

---

### Post by PlagueGiver on 2016-11-03
Strange, I'm still getting the same error! :confused:

---

### Post by gedakc on 2016-11-03
There were some bugs fixed in recent versions of the e2fsprogs package which deals with ext2/3/4 file systems.

You might try booting from the latest [GParted Live]("http://gparted.org/livecd.php") (currently 0.27.0-1) and running the e2fsck command from a terminal window.

For example

```
sudo e2fsck -fy /dev/sda1
```

or to check for bad blocks

```
sudo e2fsck -cc /dev/sda1
```

I highly recommend backing up all your data before editing partitions with any partition tool.

---

### Post by Bashing-om on 2016-11-04
PlagueGiver; Morning .

Request to know your status, 
Do you require further assistance ?

[INDENT][INDENT]here to help
[/INDENT][/INDENT]

---

