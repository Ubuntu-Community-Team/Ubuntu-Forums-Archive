---
title: "apt-get issues &amp; CD driver problem"
date: 2008-03-15
forum: General Help
---

### Post by cuulcars on 2008-03-15
I've been figuring the whole Ubuntu system out, and its had its kinks and creases I've smoothed out, and its pretty broken in now. Except for 2 things:

1.) I've used apt-get to install a few things, and its worked for the most part. But for certain things, games in particular, they don't seem to play after I install them. They appear under games in the applications menu, and I click on them, but nothing comes up. Two such examples are neverball and Dreamchess. I realized they both work in a 3d, environment, however, and was wondering if that might had something to do with it, and if so, how to fix it.

2.) When I go to computer:///, all my hard drives, CD drives, remove storage and whatnot are there, as should be. I can access my hard drives fine. But as for CD's and others, they don't seem to work. The CD drive is there, but when I put something in it, it doesn't recognized its being used. I've tried mounting the drive, but that didn't seem to do anything.

Any help is greatly appreciated.

---

### Post by Shazaam on 2008-03-15
1. Have you tried running the apps in terminal? If there is a problem this will usually spit out errors so you can fix them. Applications>Accessories>Terminal. Once that opens just enter the name of the app you want to run.
2. Open terminal, type this in and hit enter, then enter your password (you won't see it) and hit enter again. Copy/paste the output here......
```
sudo fdisk -l
```
(small L)
This will print out a list of your drives.

---

### Post by cuulcars on 2008-03-15
Okay, this is the message I get for the game:

./neverball: No available video device

and for the drivers:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x02cc02cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         629     4755208+   b  W95 FAT32
/dev/sda2   *         630       15504   112455000    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xccdbccdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19080   153260068+  83  Linux
/dev/sdb2           19081       19457     3028252+   5  Extended
/dev/sdb5           19081       19457     3028221   82  Linux swap / Solaris

---

### Post by Shazaam on 2008-03-15
Hmm. Try this, it will print out your fstab so we can see what it says about your optical drives....
```
cat /etc/fstab
```
It also looks like you need video drivers installed. Go to System>Administration>Restricted Drivers Manager and see if you can enable them.

---

### Post by cuulcars on 2008-03-15
The cat results:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0c270cac-7d04-4bda-a87a-7e1e13c7d074 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=dea93ffc-c2ba-4cbd-8766-57d9283f9e60 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

and there was a driver not enabled so I enabled it. Its downloading the package for it as I type.

---

### Post by Shazaam on 2008-03-15
Is this......
```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
```
a direct copy/paste? Or did you type it in? If it is direct, if you look real hard I think you can find the error.
If you can't, enter this in terminal.....
```
gksudo nautilus
```
This will open your nautilus file browser with FULL root access so be VERY careful with what you are doing.
Go to File System> /etc/fstab and double click it. This will open fstab for editing. Once it opens go to the lines posted above and change this.....
```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
```
to this....
```
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```
See the difference? Once you make the changes go to File>Save and save it. Reboot and see if that makes any difference.

---

### Post by cuulcars on 2008-03-15
Oh, the 0 is 1 and the 1 is 0. Thanks. But I now have a much bigger problem when I installed the graphics driver. I can't boot linux (Btw, I'm posting this from Windows, obviously)!!! I enabled the ATI graphics driver, and it said I needed to reboot, so I did. But now it starts up and shows a blank screen when it should be showing the GDM.

---

### Post by Shazaam on 2008-03-15
Argh! Sorry.
To get back to a desktop hit ctrl+alt+backspace (or ctrl+alt+F1). Once you are at the prompt type in ```
sudo dpkg-reconfigure phigh xserver-xorg
```
If it complains about that use this one.....
```
sudo dpkg-reconfigure xserver-xorg
```
and when it asks you for a video driver choose VESA and choose the default answers for the rest.
Then type in ```
sudo reboot
```

---

### Post by Shazaam on 2008-03-15
I need to run an errand but I will be back asap.

---

### Post by cuulcars on 2008-03-15
OK. Its restored now. Is it all set ready to go or was that just to allow me to get back to the desktop? Do I need to reconfigure it back to the way it was before I downloaded the driver?

---

### Post by Shazaam on 2008-03-15
Did the cdrom change help?

At this point (as I don't have an ATI card) I will have to direct you to a long post but I think if you read it through you will be able to get your card up and running. Here is the post..........

[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)

---

### Post by cuulcars on 2008-03-16
Yes it did. Thanks for the link, I'll check it out.

---

