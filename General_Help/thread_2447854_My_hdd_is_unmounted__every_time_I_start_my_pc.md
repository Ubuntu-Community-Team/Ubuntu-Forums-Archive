---
title: "My hdd is unmounted  every time I start my pc"
date: 2020-07-27
forum: General Help
---

### Post by erth-r502 on 2020-07-27
can some one help me fix this 
my hdd is unmounted every time I start my pc

---

### Post by Bashing-om on 2020-07-27
erth-r502; Hello - Welcome to the forum.

Not much info to know which direction to take here,
> 
my hdd is unmounted


Execute terminal command:
```

sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And tell us the drive designation and partition that is our target.

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by Impavidus on 2020-07-28
Technically, hard drives aren't mounted. Filesystems are mounted and filesystems typically reside on partitions and a harddrive can have zero, one or more partitions.

Linux (in contrast to Windows 8 and up, using default settings) always unmounts all storage when shutting down. This is good, as it allows other OSs to access the filesystems. When starting the OS again, the filesystems have to be mounted again before they can be used.

Is it your intention to mount particular filesystems automatically at boot? This can be configured using [fstab](https://help.ubuntu.com/community/Fstab).

---

### Post by erth-r502 on 2020-07-29
```

/dev/sda1

```

---

### Post by erth-r502 on 2020-07-29
thx you all for helping fix my problem sry for not being more specific 

I've use Disk for making my HDD mount every time i boot my pc

---

