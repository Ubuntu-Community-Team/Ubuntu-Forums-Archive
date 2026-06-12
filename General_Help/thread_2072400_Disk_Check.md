---
title: "Disk Check"
date: 2012-10-17
forum: General Help
---

### Post by otetiani on 2012-10-17
Just realized after reading the man page for fsck that I haven't seen a disk check on boot for a while even though I boot 3-4 times a day.

Using 12.04 x64 ext4 filesystem

Can anyone tell me where the setting is for the number of cycles prior to disk check is for ext4 filesystems?  I know it used to be tune2fs for ext3.

Thanks

---

### Post by oldfred on 2012-10-17
Still is, see 

man tune2fs
> If max-mount-counts is 0 or -1, the  num&#8208;
              ber  of  times  the filesystem is mounted will be disregarded by
              e2fsck(8) and the kernel.



 sudo tune2fs -l /dev/sdd3

looks like mine does not run either? 

Mount count:              117
Maximum mount count:      -1

---

### Post by ajgreeny on 2012-10-17
I have always in the past set my system to run a check every 70 - 80 bootups, as 30, the previous default, was far too frequent for my usage.  This default safety check seems to have been removed from 12.04 for some strange reason; anyone know why?  I always found this to be a bit comforting and it didn't take very long assuming there were no problems found in the filesystem.

Command ```
sudo tune2fs -c 80 /dev/sda1
```edited as you wish, is the simple way to set it how you want.  See **man tune2fs** for all available options.

---

### Post by otetiani on 2012-10-17
Thanks ajgreeny

I thought maybe a different tool was used for the ext4 filesystem and that was why it was disabled.  I too like the comfort of the check which is why I was looking into it.

---

