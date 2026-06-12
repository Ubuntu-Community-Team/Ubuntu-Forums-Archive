---
title: "Mounting failed; Device or resource busy"
date: 2006-11-27
forum: General Help
---

### Post by HYKTOTAM on 2006-11-27
good day, im new to Linux, but do have some experience with FreeBSD. my problem is as follows:

after doing upgrading linux-image-server my Ubuntu 6.06 server became unbootable. here is what i get:

Booting "Ubuntu, kernel 2.6.15-27-server'

root (hd0,0)
Filesystem type is ext2fs, partition type 0xfd
kernel /boot/vmlinuz-2.6.15-27-server root=/dev/hda1 ro quiet splash
[Linux-bzImage, setup=0x1c00, size=0x16d515]
initrd /boot/initrd.img-2.6.15-27-server
[Linux-initrd @ 0x1df0a000, 0x6a6fc4 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
mdadm: /dev/md0 has been started with 2 drives.
mdadm: /demmd1 has been started with 3 drives.
mount: Mounting /dev/hda1 on /root failed: Device or resource busy
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init

what puzzles me is the DEVICE OR RESOUCE BUSY message. as you can see i have hda1 in RAID-0 with hdb1 (md0) and sda1, sdb1, sdc1 in RAID-5 (md1). the mdadm loads both arrays fine, then something happens.

i have booted of a DSL-live-cd, sudo su, chrooted, fiddled with grub menu, downgraded the linux-image-server..... still i get the same error.

any help or advice - i really need it, since i managed to move all 3 years of company's backup to the RAID-5 disks and can't afford to lose that info.

cheers!

---

### Post by HYKTOTAM on 2006-11-29
PROBLEM SOLVED!

seems some update changed the contents of /boot/grub/menu.lst
the correct like should have read:

kernel /boot/vmlinuz-2.6.15-27-686 root=/dev/md0 ro md=0,/dev/hda1,/dev/hdb1

---

