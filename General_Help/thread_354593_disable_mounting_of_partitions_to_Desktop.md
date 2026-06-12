---
title: "disable mounting of partitions to Desktop"
date: 2007-02-06
forum: General Help
---

### Post by desheikh on 2007-02-06
Hi,

I have drive icons to my windows partitions on my desktop on Ubuntu Edgy
I want to stop the icons from appearing on the desktop but I want them to continue mounting to /media/ 
Anyone know of a way to do that? 

Heres my current fstab

# /dev/hda1
UUID=C4D46E7FD46E7418 /media/C        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=820B-63F7  /media/D        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=4496-F715  /media/E        vfat    defaults,utf8,umask=007,gid=46 0       0

Thanks,
Ali

---

### Post by Ramses de Norre on 2007-02-06
```
gconf-editor /apps/nautilus/desktop
```
And uncheck "volumes_visible".

---

### Post by mcduck on 2007-02-06
By the way, you may want to replace that '1' at the end of those windows partitions entries in fstab. '1' shoul only be for root partition, and for others you can use '2'(to run fsck on them after root) or '0'(to not check them at all).

I had the same error in my fstab after installing Edgy, and it slowed my boot to crawl..

---

### Post by desheikh on 2007-02-06
Hey thanks :D

Anyway I can have removable drives show up on the desktop but not my windows partitions?

Ali

---

### Post by mcduck on 2007-02-07
The only way is to leave the 'volumes_visible' enabled and then mount drives you don't want to show on desktop to any other directory than /media. I recommend /mnt.

---

