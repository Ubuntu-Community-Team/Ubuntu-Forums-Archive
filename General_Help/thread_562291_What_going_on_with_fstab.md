---
title: "What going on with fstab?"
date: 2007-09-28
forum: General Help
---

### Post by FrankVdb on 2007-09-28
It took me hours to add two drives to a cheap Medion computer I bought from an Aldi supermarket store here in Belgium. 

I added an IDE and an SATA drive to the existing SATA drive. The resulting PC config is pretty basic: 
/dev/hda = CD/DVD writer (IDE master)
/dev/sda = boot drive (SATA)
/dev/hdb = added IDE drive (IDE slave)
/dev/sdb = added SATA drive

I created two mount directories for the two new drives, being /media/data-a (for /dev/sdb) and /media/data-b (for /dev/hdb) and added the following entries to fstab: 

# /dev/hdb1
UUID=272dcc24-7771-42ed-8150-90fb72cdeabc  /media/data-b   ext3      auto,defaults,rw    0   0
# /dev/sdb1
UUID=3ec43a0c-73cd-46c0-974c-3281919606a1  /media/data-a   ext3      auto,defaults,rw    0   0

Fstab being poorly documented, I had been messing around with the options for an eternity. In the meantime, my lawn grew five centimeters and my hair became so long I was wondering if something was gradually dimming the light.

After some tinkering, disk "data-a" appeared in Nautilus but disk "data-b" simply refused to come up, although it was recognised by the BIOS and by Ubuntu itself. Blkid was showing it and the other drives.

I read somewhere that from Edgy upwards one has to use the disk UUID's in fstab. Maybe I'm naive in just believing what other people, who appear to be much more knowledgeable about Ubuntu, are saying, but it's plain wrong!

The IDE drive only showed up when I changed it's UUID into its regular name (/dev/hdb1).

It literally took me hours to find that out. It is strange that fstab, being so important for booting your system correctly, should be so poorly documented. The man pages (yes, I RTFM!) date back to 1999 and neither the stuff I found on the Internet nor my Linux books - among which some good ones, such as "Linux: das distributionsunabhängige Handbuch" by Plötner&Wendzel (German), and "Leerboek Linux-systeembeheer" by van Vugt (Dutch) - solved my problem. 

After that, I had to chmod both drives so that I, being user and not root, could write to the drives. That's because the default settings only provide root access to freshly installed drives... That took me at least another hour to find out. It's hard to believe I'm the only one facing those issues...

My working fstab now looks as follows (lots of comments, I know):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=40e67eee-0445-42a1-a4bb-eba40d45ba3d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0adbfb62-1b59-4661-b503-ff9462b1e4a8 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdb1
# UUID=272dcc24-7771-42ed-8150-90fb72cdeabc  /media/data-b   ext3      auto,defaults,rw    0   0
/dev/hdb1   /media/data-b   ext3     auto,defaults,rw    0   0
# /dev/sdb1
UUID=3ec43a0c-73cd-46c0-974c-3281919606a1  /media/data-a   ext3      auto,defaults,rw    0   0


By the way: is there a way to have only one user access a specific (password-protected) drive?

---

### Post by BrownCoal on 2007-09-29
This page should answer many of your questions: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Rumpty on 2007-09-29
Yes, it's useful, but not a word about UUID? I would like to know, for instance, how "sticky" is the UUID?

---

### Post by bodhi.zazen on 2007-09-29
To list devices by UUID :

```
sudo blkid
```

```
ls -l /dev/disk/by-uuid
```

What do you want to know about UUID ?

[http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

You can always fall back to /dev/sdxy or /dev/hdxy if you like ....

The uuid will change if you re-format the partition.

---

