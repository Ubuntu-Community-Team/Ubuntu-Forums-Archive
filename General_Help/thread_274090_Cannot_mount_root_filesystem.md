---
title: "Cannot mount root filesystem"
date: 2006-10-09
forum: General Help
---

### Post by Clytemnestra on 2006-10-09
Hello everyone.
On Saturday I updated my computer (Compaq v3000; kernel 2.6.15-27-k7). It has been restarted successfully several times since, but today has started hanging on "Mounting root filesystem" whenever I try to start it. This is the output:
```
Uncompressing Linux... Ok, booting the kernel.
mount: Mounting /dev/sda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```
After this, it sometimes goes to the busybox shell, but not always.
Also, I know that the drive can still be mounted with Kanotix. :rolleyes: 
I would appreciate any help that I can get.
Thank you.

---

### Post by viniosity on 2006-10-15
I am having the same issue all of a sudden.  Anyone have a solution?

---

### Post by Hygelac on 2006-10-27
We seem to have got it.  We chrooted from the Kanotix:
```
su -
mount -t ext3 -o rw /dev/sda1 /mnt
chroot /mnt
apt-get update
apt-get upgrade
```
I once chrooted to fix my Debian system; it needed some fixed packages to be bootable again.  I thought that this might do it here, but don't know why it worked; none of the packages that upgraded were relevant (just various KDE components and such).  Does anyone know how this could have fixed it?
At least it works! :mrgreen:

---

