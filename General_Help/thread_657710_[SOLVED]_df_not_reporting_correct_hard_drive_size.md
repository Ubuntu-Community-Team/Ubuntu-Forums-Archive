---
title: "[SOLVED] df not reporting correct hard drive size"
date: 2008-01-03
forum: General Help
---

### Post by eclark on 2008-01-03
This is very strange, however, I know someone out there can help me. Let me explain my problem.

Two weeks ago, this was my setup:
[INDENT]/dev/hda 60gb NTFS Windows XP x64
/dev/hdb  4gb EXT3 Ubuntu install (only 3.8gb of recognized space)[/INDENT]


I decided over the holidays that I wanted to get rid of the 4gb hard drive and replace it with a 120gb hard drive I had. (all IDE drives) The 120gb was NTFS and has a lot of raw AVI files on it, it's just a storage hard drive and I didn't want to reformat it. What I did was resize the 60gb NTFS hard drive (/dev/hda) using ntfsresize and qtparted so now it was a 30gb NTFS + 26gb EXT3 + 1gb swap = (~60gb). I followed the directions here [http://nishants.net/articles/ntfsresize.htm]("http://nishants.net/articles/ntfsresize.htm")

At this point here was my setup:
[INDENT]/dev/hda1 30gb NTFS Windows XP x64
/dev/hda2 26gb EXT3 blank
/dev/hda3 1gb swap
/dev/hdb   4gb EXT3 current ubuntu install[/INDENT]

I was thinking that rather than backing up all my data, installing a whole new operating system, and then reconfiguring linux to my taste, what I would do is run:

```
dd if=dev/hdb of=dev/hda2 bs=1
```

So basically what I did was copy the whole OS from the 4gb onto the new partition I was going to use. Yes, I know this copied EVERYTHING :)

So, yesterday, I tried to run the update to Gutsy (7.10) and it stopped like half way because I didn't have any space! I knew something was wrong so I did this (output included)

```
emery@actuality:~$ df -h /dev/hda2
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             3.8G  3.5G   88M  98% /
```

I knew this wasn't right because the 4gb was not even in the computer. So I ran this: (output included)

```
emery@actuality:~$ sudo fdisk /dev/hda -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3917    31457280+   7  HPFS/NTFS
/dev/hda2            3918        7170    26129722+  83  Linux
/dev/hda3            7171        7297     1020127+  82  Linux swap / Solaris
```

Hmmmm... not really adding up at this point. Both these commands were run from the same terminal, right after each other. 

Next, I went into /etc/fstab, realized that I needed to update it to reflect the new /dev/hda2 hard drive that my root system was on, made the changes and restart. Same results as above.

Here is my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                 /proc           proc          defaults        0       0
/dev/hda2       /                   ext3    defaults,errors=remount-ro 0       1
/dev/hda3 	none           swap    sw              0       0
/dev/hdc         /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/fd0         /media/floppy0  auto    rw,user,noauto  0       0

So..... this is where I am now. I am thinking it has to do something with the fact that I copied my whole operating system from one hard drive to another. I bet there is some config file somewhere that has stored the size of my old drive. The problem is that I don't know where this file is or how to update it with the correct size of my new hard drive. Even the "Computer - File Browser" in Gnome reports that I only have 87.0MB of space left!

I also have several other hard drives connected. Two NTFS sata drives that mount fine. (/dev/sda and /dev/sdb) I do not include them in the fstab because I do not want to mount them every time I boot. (also I do not have ntfs-3g installed) I also have a 500gb external usb drive that I plug in when using. This is fat32 and it also mounts fine (-rw, usually /dev/sdc). I am not sure if either of them have anything to do with the problem, but maybe so.

Neither me nor my roommate can figure out what to do. I read these forums all the time but this is my first post on here. I know there is an answer out there. Let me know if you want me to do anything. Any help is appreciated. Thanks a bunch!
Emery

---

### Post by sciencewhiz on 2008-01-03
when you used dd, you copied the entire filesystem, including the size. You should be able to resize the filesystem to the full partition size using qtparted/gparted.

---

### Post by eclark on 2008-01-03
> **sciencewhiz said:**
> when you used dd, you copied the entire filesystem, including the size. You should be able to resize the filesystem to the full partition size using qtparted/gparted.

Hmm... maybe I don't understand the fundamentals of the filesystem. Here is my screenshot of qtparted:

[CENTER][IMG]http://emdog4.googlepages.com/qtparted01.png[/IMG][/CENTER]

---

### Post by sciencewhiz on 2008-01-03
Try checking the file system. Boot with your install CD and run the following command:

```
fsck /dev/hda2
```

---

### Post by geirha on 2008-01-03
You can use resize2fs to enlarge the ext3 filesystem to use the entire partition. Read ```
man resize2fs
```

---

### Post by eclark on 2008-01-04
thanks guys! got it working and learned something else new about linux.

Here is what I did:

```
emery@actuality:~$ sudo fdisk -l /dev/hda
Password:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3917    31457280+   7  HPFS/NTFS
/dev/hda2            3918        7170    **26129722+**  83  Linux
/dev/hda3            7171        7297     1020127+  82  Linux swap / Solaris

```

then
```
sudo resize2fs -p /dev/hda2 653243
```

I also found out that resize2fs uses 4k block sizes rather than the 1k block sizes as are reported in the "sudo fdisk - /dev/hda2" (notice bold) so what I had to do is divide 26129722/4 = 653243.5. You can see what I put for the resize2fs command.

Now I am reporting:
```
emery@actuality:~$ df -h /dev/hda2
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              25G  3.6G   20G  16% /
```

which is what it should be :)

Thanks for the help guys. I knew it could be done! The reason I use Ubuntu is because of the support on the internet, it is awesome. thanks again!
Emery

---

