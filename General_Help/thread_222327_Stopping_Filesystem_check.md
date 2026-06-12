---
title: "Stopping Filesystem check"
date: 2006-07-24
forum: General Help
---

### Post by ihavenoname on 2006-07-24
I am sorry but this is probably the most annoying thing on Ubuntu right. (for me) It keeps telling me my hda1(fat 32) partion is corrupt or something about my mbr back being diffrent. This delays my start-up  by 2-3 minutes (estimate). Is there anyway to turn this off? (Do I edit some script?? I am totally lost here) I tryed a sysv editor but it didn't really help. Any suggestion on how to disable this check?

---

### Post by JoWilly on 2006-07-24
> **ihavenoname said:**
> I am sorry but this is probably the most annoying thing on Ubuntu right. (for me) It keeps telling me my hda1(fat 32) partion is corrupt or something about my mbr back being diffrent. This delays my start-up  by 2-3 minutes (estimate). Is there anyway to turn this off? (Do I edit some script?? I am totally lost here) I tryed a sysv editor but it didn't really help. Any suggestion on how to disable this check?

Put 0 0 at the end of your hd line in /etc/fstab to disable the check.

You can also stop the check at boot with ctrl-c.

---

### Post by reacocard on 2006-07-24
you'll need to edit your fstab:
```
sudo gedit /etc/fstab
```

change the last number for each entry to 0 to disable filesystem checking.

---

### Post by ihavenoname on 2006-07-24
The first is my fstab as it is now. The second is the way I interperted your responses. (Btw thanx for the speed of your responses.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hdc1       /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

into 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       0 
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hda2       /media/hda2     ext3    defaults        0       0
/dev/hdc1       /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto 0       0
```

---

### Post by JoWilly on 2006-07-24
> **ihavenoname said:**
> The first is my fstab as it is now. The second is the way I interperted your responses. (Btw thanx for the speed of your responses.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ext3    defaults        0       2
/dev/hdc1       /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

into 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       0 
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hda2       /media/hda2     ext3    defaults        0       0
/dev/hdc1       /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto 0       0
```

That's it, but you should leave the fsck "at least" on the root partition and any partition containing important data.

---

### Post by ihavenoname on 2006-07-24
So change the root partion back to 0 1? (Sorry I know next to nothing when it comes to this type of stuff.)

---

### Post by JoWilly on 2006-07-24
> **ihavenoname said:**
> So change the root partion back to 0 1?

Yes, that's it.

---

### Post by mmcmonster on 2006-07-24
> **ihavenoname said:**
> I am sorry but this is probably the most annoying thing on Ubuntu right. (for me) It keeps telling me my hda1(fat 32) partion is corrupt or something about my mbr back being diffrent. This delays my start-up  by 2-3 minutes (estimate). Is there anyway to turn this off? (Do I edit some script?? I am totally lost here) I tryed a sysv editor but it didn't really help. Any suggestion on how to disable this check?

Actually, this sounds a little worrysome.  Maybe the filesystem problem is something that can be fixed?  Better to fix the problem and let the occasional filesystem check go through than risk losing serious amounts of data/time because of a corrupt filesystem.

Can you copy down the error message verbatim and post it?  I'm not a great filesystem expert or anything, but there are a lot of them around here. ;-)  If no one can help you here, there is always google. :-)

---

### Post by ihavenoname on 2006-07-24
> **mmcmonster said:**
> Actually, this sounds a little worrysome.  Maybe the filesystem problem is something that can be fixed?  Better to fix the problem and let the occasional filesystem check go through than risk losing serious amounts of data/time because of a corrupt filesystem.

Can you copy down the error message verbatim and post it?  I'm not a great filesystem expert or anything, but there are a lot of them around here. ;-)  If no one can help you here, there is always google. :-)
Thanx all for helpping me fix the intteruption during boot up. mmcmonster you are right I should look to find out what the problem is. There error is not really a filesystem one. It has to do with the back-up of the mbr not matching the actual mbr. It mostly consists of numbers. If anyone could tell me how to save a console output to a text file I would be glade to post it. I am not sure if it will be in the log files I will have to check. I actually have two huge tests to study for, so I need to get to that but as soon as I can I will attempt to fix the issue. I just needed a way to disable the check for now as it only occurs on Ubuntu, and thus keeps me from using Ubuntu because other things start much faster. (arch starts in btwn 25-35 seconds based on what I have running. And fedora is 55 seconds. Window is 35 (not including the 2 minutes of loading after the desktop is visable.) Ubuntu is usually 45 but with the error it was more like 3min 45 seconds.) Any ways thank you everyone for your help and suggestions.

---

### Post by ihavenoname on 2006-07-29
It works thank you all for your help.

---

