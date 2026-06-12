---
title: "Mounting Volumes"
date: 2008-07-07
forum: General Help
---

### Post by problemes on 2008-07-07
I have installed Debian on my PC and I'm totally a beginner at all the linux world. after installing Debian .I couldn't mount the partitions. so I read almost every thing about "Mounting volumes" but I couldn't know how to mount it until now after spending a lot time in surfing the net and in searching.

so please help me. 
and it will be great to know how to mount by using the graphical interface. if not "Terminal window" will be OK.!!

And thanks a lot in advance.

---

### Post by Titan8990 on 2008-07-07
There will be no getting around using some terminal. If your one of those people that can't stand using a command line, go back to Windows or MAC OS X. There are two way you can mount a drive and even the GUI method requires you start from the shell.

GUI Method:

$sudo nautilus

Right click on the drive you want to mount and select "Mount Volume".

The more powerful and effective method:

$sudo fdisk -l

shows an ouput like this:

```
jordan@einstein:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29920   240332368+  83  Linux
/dev/sdb2           29921       30401     3863632+  82  Linux swap / Solaris
```

Here you can see what drive you are wanting to mount got assigned which letter. 

So if you wanted to mount sda1 it would go something like this:

$sudo mkdir /media/sda1
$sudo mount /dev/sda1 /media/sda1

You will then be able to view your drive at /media/sda1/.

---

### Post by forger on 2008-07-07
well... nautilus in the latest ubuntu (hardy heron 8.04) has mount support, you simply go to Places > Computer > Right-click on the hard drive you want and choose "Mount volume" or "Unmount volume"

edit: look the post before this one

---

### Post by Titan8990 on 2008-07-07
I don't think it will let you mount a hard disk volume unless you are root hence the $sudo nautilus in my post.

---

### Post by forger on 2008-07-07
For debian, you have to install **gnome-mount** package:
[http://packages.debian.org/search?keywords=gnome-mount](http://packages.debian.org/search?keywords=gnome-mount)

Now, the problem is that you should use something more desktop-wise instead of debian, which more security-wise :) It will help you a lot if you install or try out the latest ubuntu, which is based on debian

---

