---
title: "Mounting Windows Software raid 0 in ubuntu"
date: 2014-02-16
forum: General Help
---

### Post by xencored2 on 2014-02-16
Howdy all ive been following this post here [http://ubuntuforums.org/showthread.php?t=833653&p=5217561#post5217561](http://ubuntuforums.org/showthread.php?t=833653&p=5217561#post5217561)
But when mounting I keep getting this error

sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdb3 /dev/sda3
mdadm: array /dev/md0 built and started.
root@xbmc-System-Product-Name:~# sudo mount -t ntfs /dev/md0 /home/xbmc/Media   NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@xbmc-System-Product-Name:~#

Any idea why? I really don't want to lose the data if I can help it.
Thanks

---

