---
title: "trouble with external hard drive"
date: 2007-08-09
forum: General Help
---

### Post by AJS302 on 2007-08-09
i recently bought a 320gb maxtor external hard drive it mounts ok i can also read from it ok but it says i do not have permission to write to it, can anyone help my with this?

thanks

---

### Post by apetresc on 2007-08-09
> **AJS302 said:**
> i recently bought a 320gb maxtor external hard drive it mounts ok i can also read from it ok but it says i do not have permission to write to it, can anyone help my with this?

thanks
This is a common problem, easy to fix, and 99.9% chance that it's caused by the way it gets mounted. Paste the contents of your /etc/fstab file. :)

---

### Post by AJS302 on 2007-08-09
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=96bcf5c7-1b8c-418e-9f49-4e265a0625a2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=27a61e66-7245-40a8-a8b5-34934c4833ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by splintercellguy on 2007-08-09
Does the external have an NTFS partition? If that is the case, please do

sudo apt-get install ntfs-config

and go to System -> Administration -> NTFS Config

and enable external mounting.

---

### Post by apetresc on 2007-08-09
Ookay, the file's not in your fstab at all. Please plug it in as you usually do (at the point where you can read it, but not write it), and paste the output of the "mount" command. Just "mount", no parameters.

---

### Post by logos34 on 2007-08-09
> **splintercellguy said:**
> Does the external have an NTFS partition? If that is the case, please do

sudo apt-get install ntfs-config

and go to System -> Administration -> NTFS Config

and enable external mounting.

That's just the gui--you'll need the driver as well
[B]
sudo apt-get install ntfs-3g[/B]

That is, if we're dealing with an NTFS partition

---

### Post by logos34 on 2007-08-09
> external hard drive it mounts ok i can also read from it ok but it says i do not have permission to write to it, can anyone help my with this?

what does the following show:

**ls -l /media/<yourdisk>**

?

---

