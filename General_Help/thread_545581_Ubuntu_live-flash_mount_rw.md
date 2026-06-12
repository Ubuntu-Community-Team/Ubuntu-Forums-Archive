---
title: "Ubuntu live-flash mount r/w"
date: 2007-09-07
forum: General Help
---

### Post by xanderfiss on 2007-09-07
I am working on a flash drive based off of the live-cd.  It boots off of GRUB and for the most part everything works beautifully.

By default the flash drive fstype (FAT16) is automatically detected and the drive is mounted to /cdrom as read-only.  I need to be able to access this partition as read/write, and I'm not sure which files I need to edit to make this happen.

Thanks!

Xander

---

### Post by xanderfiss on 2007-09-07
I'm thinking it's

/usr/share/initramfs-tools/scripts/casper-premount/10driver_updates

gonna try that now, if anyone has an idea let me know

---

### Post by xanderfiss on 2007-09-07
Ok, so that didn't work.  /cdrom isn't even in the mount table, so I'm at a loss on what to do.

---

### Post by xanderfiss on 2007-09-11
Okay! So I figured it out, in case anyone is curious, even though I didn't get any replies.

If you are using the Feisty live-CD to make a live-flash and you want that flash drive to be read/write, do the following.

`fdisk -l` and find out what device/partition your flash drive is, e.g. /dev/sdd1

`sudo nano /etc/mtab' and add the following line at the bottom:

/dev/sdd1 /cdrom vfat ro 0 0

This is descriptive of what it's currently doing, mounting the flash drive read-only into /cdrom as type vfat.  Then run:

`sudo mount -t vfat -o rw,remount /dev/sdd1 /cdrom`

and BOOM! you have r/w access.

---

