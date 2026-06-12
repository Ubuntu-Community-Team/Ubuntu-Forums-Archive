---
title: "can't mount external drive"
date: 2018-10-13
forum: General Help
---

### Post by Lloydb39 on 2018-10-13
I have a hard drive from an old laptop that I'm trying to read but it won't mount via USB. Disk utility can see it.
I did this and got this:
```
lloyd@linux:~$ sudo mount /dev/sdb /mnt
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or helper program, or other error.

```Can anyone tell me what to do next?

---

### Post by ajgreeny on 2018-10-13
What is the output of **sudo fdisk -l** with the disk attached?

---

### Post by Lloydb39 on 2018-10-13
for this drive only
> Disk /dev/sdb: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xfe374338




---

### Post by sudodus on 2018-10-13
I would expect a list like this with one or more partitions /dev/sdb1, /dev/sdb2 ...

```
Device         Start        End    Sectors  Size Type
/dev/sdb1       4096    1048575    1044480  510M EFI System
/dev/sdb2    1048576   11534335   10485760    5G Linux filesystem
```

Otherwise there are no partitions or maybe a damaged partition table. Anyway, nowadays we are not keeping file systems directly at the drive head (like in /dev/sdb), but in partitions. So find or create a partition (for example with **gparted**), and mount it something like

```
sudo mount /dev/sdb**1** /mnt
```

---

### Post by Lloydb39 on 2018-10-13
OK, well here's the whole thing:
```
lloyd@linux:~$ sudo fdisk -l
[sudo] password for lloyd: 
Disk /dev/loop0: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 42.1 MiB, 44183552 bytes, 86296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 87.9 MiB, 92119040 bytes, 179920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00006dbe


Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *            63 1936860659 1936860597 923.6G 83 Linux
/dev/sda2       1936860660 1953520064   16659405     8G  5 Extended
/dev/sda5       1936860723 1953520064   16659342     8G 82 Linux swap / Solaris


Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.








Disk /dev/sdb: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xfe374338
lloyd@linux:~$ 

```I thought I already had created a partition with gparted but I'll try again and then try to mount again. My first post showed what it did last time. 
Update. With a partition it is now mounted and shows on my desktop, but won't let me put files on it. Says I'm not the owner. Thanks

---

### Post by sudodus on 2018-10-13
Still no partition is found in /dev/sdb. I'm waiting for the result after you try again with gparted. Good luck :-)

If you have no luck with gparted, the drive might be damaged. Please check the S.M.A.R.T. status according to this link,

[S.M.A.R.T. information of HDD and SSD](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors-what-should-i-do-now/972983#972983)

and analyze the problem (and try more) according to the following link,

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by sudodus on 2018-10-13
We cross-posted :-P

I understand that you have a partition now, and that it can be mounted read-only or maybe mounted by root (the superuser).

What file system is it? **ext4** or some other linux file system or **NTFS** or **FAT32** or some other Microsoft file system?

---

### Post by Lloydb39 on 2018-10-13
Sorry. I made it ext4
do I use "chown" to be able to "own" it?

---

### Post by sudodus on 2018-10-13
You have full flexibility with ext4 :-)

I suggest that you create one or more subdirectories

```

sudo mkdir /mountpoint/dirname1
sudo mkdir /mountpoint/dirname2
...

```

and then change owner

```

sudo chown $USER /mountpoint/dirname1
sudo chown $USER /mountpoint/dirname2
...

```

and after that your user ID ($USER) should have both read and write permissions in the subdirectories.

---

### Post by Lloydb39 on 2018-10-13
Well obviously I'm doing something wrong. I did this while on the drive:
> lloyd@linux:/media/lloyd/767033c0-af46-40dc-ab6f-9e9ea6cb9d42$ sudo mkdir /mountpoint/dirname1
[sudo] password for lloyd: 
mkdir: cannot create directory &#8216;/mountpoint/dirname1&#8217;: No such file or directory
lloyd@linux:/media/lloyd/767033c0-af46-40dc-ab6f-9e9ea6cb9d42$ 

So still no access.

---

### Post by sudodus on 2018-10-13
Sorry, I did not not explain:

**/mountpoint** is a generic name. You must use the actual path and name of the mount point. Check with

```
sudo lsblk -f
```

to find the actual name of the mount point.

And you may prefer better names than **dirname1** ...

Edit:

It seems the mountpoint is

```
/media/lloyd/767033c0-af46-40dc-ab6f-9e9ea6cb9d42
```

But please check it.

---

