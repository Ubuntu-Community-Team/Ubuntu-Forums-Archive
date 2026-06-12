---
title: "Renaming hard disk partitions in Ubuntu 7.10"
date: 2008-03-26
forum: General Help
---

### Post by AmpersUK on 2008-03-26
I dual boot with Windows XP.

I have three 500GB SATAY hard drives in my machine with the last having a partition being used by Ubuntu.

I have 9 other partitions, C, D, E, F, G, H etc

To aid memory, I would like to include _C, _D, _E after each of the drives as they show up in Ubuntu but whenever I try to add the letter Ubuntu won't let me change the name. I do find not having such identification a little confusing

Before I "Dynotape" which drive is which and have the plastic stickers  plastered all over my keyboard, is there a better way?

Ampers.

---

### Post by spych102 on 2008-03-26
To do this permanently you need to edit your the file /etc/fstab, which controls all mount locations, be careful though!!

[LIST=1]
[*]Open a terminal: Applications -> Accessories -> Terminal
[*]Backup the old fstab:
```
sudo cp /etc/fstab /etc/fstab_backup
```
[*]Edit fstab:
You can change, for instance, media/hdb1 to media/C in this file. Read [here]("http://www.tuxfiles.org/linuxhelp/fstab.html") for details on how this file works. Be careful not to change the partition that is mounted as "/".
```
sudo gedit /etc/fstab
```

[*]Save fstab: File -> Save
[*]Remount fstab
```
sudo mount -a
```
[/LIST]

---

### Post by spych102 on 2008-03-26
Oh yeah, I missed step 4b (sorry :???:)

4b. Create folders in  /media that bear the same names as those you are mounting.

For instance:

```
sudo mkdir /media/C
```

I trust this helps!

---

### Post by AmpersUK on 2008-03-27
Thanks, I got into the file fstab but nothing like all my hard disks are shown, however I can see them in the middle pulldown menu of my home screen.

However I found Tux very, very interesting and have bookmarked it for later research.

Ampers.

---

### Post by lswest on 2008-03-27
Do the drives automatically get mounted when you boot?  if so, there should be entries in /etc/fstab for each partition, if you could post the results of ```
cat /etc/fstab/
``` in this thread we could help you out more.  (the code just prints out the content of the file, just so you don't accidentally delete or change something)

---

### Post by AmpersUK on 2008-03-27
Thanks, I have taken a copy as requested.

Ampers

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=0900c23e-0a1b-4c43-8d9e-1275c18a2c5b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=f135ef09-4434-40b6-9281-fd10b7be5510 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by spych102 on 2008-03-27
That's strange, you only seem to have 2 partitions listed. Are your other partitions USB by any chance?

---

