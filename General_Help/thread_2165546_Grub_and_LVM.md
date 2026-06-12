---
title: "Grub and LVM"
date: 2013-08-05
forum: General Help
---

### Post by hojjat on 2013-08-05
After messing up my /boot directory, I finally managed to recover my Ubuntu installation. Right now, this is how it is:

/dev/sda is the hard disk, which has the following partitions:
/dev/sda1 is a bootable ext2 partition
The rest of disk is /dev/sda2 which is an extended volume
on top of itis /dev/sda5 which is an encrypted volume
on top of that, is /dev/dm-0 which is a LVM2 volume

This last volume, is where my / is located, which also includes /boot

Now, here is the problem: when a new linux image is installed, it gets installed in /boot (which is in /dev/dm-0), but because grub is installed to look at /dev/sda1, it won't see the new linux image.

I think the solution will be one of the following:

1) To make grub look at /boot that is /dev/dm-0
2) To make the linux images install into /boot that is on sda1

I think (not sure) that before I missed up my ubunutu, scenario (1) was the case. Anyways, I don't know how to do 1 or 2. Any help is appreciated.

---

### Post by hojjat on 2013-08-05
Actually, I found the solution is very simple! All I had to do was modify /etc/fstab to mount /dev/sda1 as /boot

---

