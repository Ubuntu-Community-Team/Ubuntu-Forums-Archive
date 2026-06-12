---
title: "[SOLVED] Disk mounting"
date: 2008-04-04
forum: General Help
---

### Post by agaudio on 2008-04-04
I have three questions regarding mounting in Ubuntu 7.10 using Gnome.

1) Is it possible to hide volumes from the left panel in Nautilus and the Disk Mounter Applet in the panel? I have a 16 Mb Dell Utility partition that I don't want to remove, but that I don't really need to see all the time. 

2) My other partitions have been named automatically so that they look like this:

```
34.2 GB Volume: MUSIC
```

Is it possible to rename the volume simply Music?

3) Why is it that if I leave an external USB hard drive plugged in, it mounts correctly when the first person logs into the computer for the day, but when that person logs out, another logs in, and then the original person logs in again, I get two links to the USB drive in the left panel in Nautilus? They both appear to lead to the same folder in /media/. On occasion, a different oddity occurs, in that there is an empty folder with the USB drive name (BACKUP) under /media/ and a new mount point for the USB drive BACKUP_ is used. It is as if all the logging in and out resulted in the mount point not being removed.

Any help on these issues would be greatly appreciated. Thanks!

---

### Post by zvacet on 2008-04-04
1. In nautilus>view>uncheck side bar and to remove applet from panel right click on it>remove from panel

Other things I don´t know.

---

### Post by agaudio on 2008-04-04
Hi, thanks for the response, but what I was really aiming at was trying to hide the specific partition but still see all the others.

---

### Post by kesman on 2008-04-04
You should first check what's the name of the partition you want to disable. You can see this with command
```

sudo mount

```
in terminal. It gives you list of all mounted filesystems. After this, you've probably found out that the 16mb partition is named as /dev/hdaX or /dev/sdaX wheter its an IDE or SATA/SCSI-hdd and X being the number of partition. I'll call it /dev/hda1 now, but replace this with your own.
Now check out /etc/fstab -file, it contains the options for mounting partitions while booting. Remove the line mounting /dev/hda1 to /media/whatever.
**REMEMBER TO REPLACE /dev/hda1 WITH THE REAL 16MB PARTITION, SINCE REMOVING ACTUAL /dev/hda1 MIGHT CAUSE YOU SEVERAL PROBLEMS**

---

### Post by agaudio on 2008-04-04
Hello, and thanks for the reply. Actually, the drive is not mounted at bootup. It just appears as mountable in the left panel. In other words, there is no entry in fstab......

---

### Post by logos34 on 2008-04-04
> **agaudio said:**
> 
Is it possible to rename the volume simply Music?

try

sudo tune2fs -L Music /dev/sda1 

or whatever the partition is

---

