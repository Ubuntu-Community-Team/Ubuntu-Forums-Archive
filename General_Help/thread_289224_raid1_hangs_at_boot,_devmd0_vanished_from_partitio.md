---
title: "raid1 hangs at boot, /dev/md0 vanished from partition table"
date: 2006-10-30
forum: General Help
---

### Post by gerryg on 2006-10-30
Hi there,

I recently installed Ubuntu 6.10 and had configured a software raid 1 array, which was working fine so far. But now the system hangs during boot after displaying "md: raid1 personality registered for level 1".

Just before that problem occured, I was doing two things:
* manually removing an obsolete entry in /boot/grub/menu.lst
* adding a startup script for my internet connection ([http://howto.htlw16.ac.at/at-highspeed-howto-2.html#ss2.18](http://howto.htlw16.ac.at/at-highspeed-howto-2.html#ss2.18))

In fact, the "/dev/md0" entry vanished from my partition table (it was there before). Could it be that one of the actions of above did that? And that this is the cause of the hang?

Does anybody know how I could at least get my machine booting successfully?

I already tried to remove the mdadm boot service and also changed the partition type from "Linux raid autodetect" (FD) to "Linux" (83), but it didn't help.

Many thanks in advance,
Gerald

---

### Post by gerryg on 2006-11-01
Hi again,

due to my insufficient knowledge of md, I was rather on the wrong track...

The problem was in fact a wrong UUID in the mdadm.conf file of the initrd image.

The solution is very well described in the thread [Software RAID and Upgrade from 6.06 to 6.10]("http://ubuntuforums.org/showthread.php?t=287723") - many thanks to the guys there!

Gerald

---

