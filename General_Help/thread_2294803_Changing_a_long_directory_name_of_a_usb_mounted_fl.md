---
title: "Changing a long directory name of a usb mounted flash drive to a short one?"
date: 2015-09-13
forum: General Help
---

### Post by pandoragami on 2015-09-13
[ATTACH=CONFIG]264397[/ATTACH]

Above I have a pic of the folder for my flash drive with a very long file name. The problem I have is how do I make it shorter (because Hugin can't work with colons and long file names). I've tried using Nautilus simply by renaming it but something else is using it; obviously it's mounted. 

How would it be possible to first unmount the drive and then change the name from "usb-Kingston_DataTraveler_3.0_00190F0C02A9BE11099E2704-0:0-part1" to "usb-Kingston" instead?

---

### Post by sudodus on 2015-09-13
Welcome to the Ubuntu Forums :-)

You can use ***gparted*** or some other tool to ***create a new label or change the label*** of the partition in the drive. The next time it is mounted automatically it should use the label instead of that long name. Make a short but good label. I think FAT and NTFS partitions can have max 11 characters in the label, ext partitions can have max 16 characters.

---

### Post by HermanAB on 2015-09-13
Just make a soft link to it.  It can be a single character, e.g. 'x':
(ln -s targetname linkname)
$ cd ~
$ ln -s /wherever/the/heck/it/is x

---

### Post by efflandt on 2015-09-13
Which Ubuntu version are you running, or do you have an entry in /etc/fstab for mounting that? Partition(s) in 14.04 USB mass storage is usually auto mounted under /media/your_username/ by either their UUID (short in this case for FAT32) if there is no partition label, or partition label if there is one. Example:```
efflandt@XPS-8100-1404:/media/efflandt$ ls -al
total 12
drwxr-x---+  3 root     root     4096 Sep 13 10:51 .
drwxr-xr-x   3 root     root     4096 Dec 30  2014 ..
drwx------  12 efflandt efflandt 4096 Dec 31  1969 7170-C7DD

efflandt@XPS-8100-1404:/media/efflandt$ ls -al
total 12
drwxr-x---+ 3 root     root     4096 Sep 13 10:56 .
drwxr-xr-x  3 root     root     4096 Dec 30  2014 ..
drwx------  8 efflandt efflandt 4096 Dec 31  1969 POWERPOINT
```And for a different shorter relative path you could create a symbolic link to it somewhere:```
efflandt@XPS-8100-1404:~$ ln -s /media/efflandt/POWERPOINT pp

efflandt@XPS-8100-1404:~$ ls -l pp
lrwxrwxrwx 1 efflandt efflandt 26 Sep 13 11:14 pp -> /media/efflandt/POWERPOINT

efflandt@XPS-8100-1404:~$ ls pp
Presentations
System Volume Information
```

---

### Post by pandoragami on 2015-09-13
@Efflandt, I'm using 14.04 LTS. My disk was formatted NTFS because FAT32 was having "splicing IO errors" while transferring photos. I named it EXTERNAL with the disk utility, not sure why it ended up in /mnt.

@ sudodus

I got gparted but I've been only able to change the label, not the "Mount Point", see below. 

[ATTACH=CONFIG]264409[/ATTACH]

---

### Post by sudodus on 2015-09-14
You must unmount the partition and mount it again in order to change its mount point. The easiest way is probably to 'eject it safely', and after that unplug it and finally plug it in again. Please check if it works that way to make it use the label when mounting!

If it does not use the label when mounting, I think that you are not automounting it, but that you have an entry in your /etc/fstab file, or use some other way to 'force' it.

---

### Post by pandoragami on 2015-09-14
@sudodus

I tried unmounting it with gparted, then using the disks utility to "power down" the drive after changing the name of the mount file in /mnt with nautilus to "x". Then I reconnected the drive and the long name was used again by the system. I looked into the /etc/fstab.d folder with nautilus and there is nothing inside it?

---

### Post by sudodus on 2015-09-14
**/etc/fstab** is a file (I have not heard of any /etc/fstab.d folder, that must be very unusual). There is a manual for it, ```
man fstab
```

Which version of Ubuntu are you running?

What flash drive is it?

Please post the output of the following commands

```
df
```

```
sudo lsblk -fm
```

---

### Post by pandoragami on 2015-09-14
@sudodus, there's an easy solution after all. If you go inside the *gnome disk utility* and click under "more actions" (graphically shown by gears) you get a drop down menu with "edit mount options" and then I just changed the mount point entry to /mnt/EXTERNAL. 

Works now, thanks all of you for trying to help.

---

