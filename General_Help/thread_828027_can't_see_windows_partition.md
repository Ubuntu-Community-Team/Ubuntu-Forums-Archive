---
title: "can't see windows partition"
date: 2008-06-13
forum: General Help
---

### Post by steve984 on 2008-06-13
I installed hardy on a 250 gb drive with windows xp. I can't see the windows files or the drive. I installed the ntfs programs but it don't show up when I look in computer any help would be appriciated. steve

---

### Post by ubtBaba on 2008-06-13
I had the same problem check out this post

[http://ubuntuforums.org/showthread.php?t=816151](http://ubuntuforums.org/showthread.php?t=816151)

This solved my problem, let me know if you need more help.

---

### Post by steve984 on 2008-06-13
i tried to do waht it says but when i checked  fdisk it shows its mounted(i only have one drive) it says ntfs/htfs files sysytem I uploaded the ntfs utlities and checked for read write permission . also I trid to load the disk manger but it says it can't find the program thanks steve

---

### Post by drs305 on 2008-06-13
Joeb454 has an easy method to automount NTFS partitions. I don't know if the ntfs apps you installed are the same as he mentions:
[HowTo: Automount NTFS Drives]("http://ubuntuforums.org/showthread.php?t=785263")

---

### Post by ubtBaba on 2008-06-13
I don't think Disk Manager is compatible with Hardy Heron.

Can you print out the contents of your fstab file

sudo nano /etc/fstab

Warning don't change anything unless you are sure you know what you are doing.

Just copy & paste for now.

---

### Post by steve984 on 2008-06-14
i did a search and I found my mp3's under /host , So it see's it I can do it that way  gutsy put it so I could get to it thru the file system though but this will work thanks steve

---

