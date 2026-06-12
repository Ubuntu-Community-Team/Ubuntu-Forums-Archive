---
title: "Boot Stops at BusyBox after disabling Secure Boot"
date: 2013-09-24
forum: General Help
---

### Post by MasterRolfe on 2013-09-24
Hi all.  I've been struggling with this problem for a couple days now.  After a regular update, my laptop complained of having a full boot folder.  Thinking I would deal with it later, I shut down normally, and since then haven't been able to get the system running again.

Originally, after selecting Ubuntu (or any older kernels - recovery mode or not) from grub, the screen would just go blank (or purple-ish).  I eventually turned off the Secure Boot feature of my Lenovo laptop, and then after selecting any version of Ubuntu, I'll land in BusyBox.  I have no idea what to do from there.

I can boot from my Live USB.  It was suggested that I reinstall grub, but while following these instrictions:

> 
Originally Posted by **hhoyt**                     [URL="http://ubuntuforums.org/showthread.php?p=9789138#post9789138"][IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]

[/URL]possibly best to reinstall grub2.
boot your install disk.

from root

1) blkid
< find the partition you installed ubuntu on
2) mount /dev/sdax /mnt      <<< where x is partion #   containing ubuntu and 'a' assumes this is your first hard drive (if have   > 1)
3) mount --bind /sys /mnt/sys
4) mount --bind /dev /mnt/dev
5) mount --bind /proc /mnt/proc
6) chroot /mnt
7)update-grub 
8) grub-install /dev/sda    <assumes the you want grub to be installed on your first hard drive ('a')
9) reboot

{from: [http://ubuntuforums.org/showthread.php?t=1561735&page=2](http://ubuntuforums.org/showthread.php?t=1561735&page=2)}


I get stuck at #6, chroot /mnt. I'm told that /bin/bash is not available (or some such).

Any help would be appreciated.  I know I could format and start again, but I really rather wouldn't.

---

