---
title: "Ubuntu hangs after physically swapping some hard disks"
date: 2007-10-20
forum: General Help
---

### Post by Tom Trommelaar on 2007-10-20
I am running Ubuntu and Windows XP using dual boot (GRUB). I recently changed my hardware configuration of hard disks from:

IDE:
1st master: dvd-rom drive
1st slave: 40gb  (boot partition, Win XP)
2nd master: 200 gb hard disk
3rd master: another dvd-rom drive
SATA:
320 gb hard disk (grub config is stored here together with Ubuntu install)

to:

IDE:
1st master: 40gb (boot partition, Win XP)
1st slave: 200 gb hard disk
2nd master: dvd-rom drive
2nd slave: another dvd-rom drive
SATA:
320 gb harddisk (grub config is stored here together with Ubuntu install)

Now both Ubuntu and Windows XP won't start. Ubuntu just crashes when the word "Kernel alive" is showing at the bottom, and Windows throws a quick blue screen and reboots.

Any ideas on how to fix this without reinstalling everything?

---

### Post by chrisccoulson on 2007-10-20
If you know which partition your root filesystem is on, you can mount it from the live CD and post the contents of your /etc/fstab and /boot/grub/menu.lst. This is definately fixable, at least for Ubuntu anyway. I take it from your post that Grub is still running and it at least knows where your menu.lst is, which is a good start.

If you boot to the live CD, open a terminal and do the following:

```
sudo mkdir /media/root
sudo mount -t ext3 /dev/xxxx /media/root
```

where /dev/xxxx is the device node for your root filesystem. Only you will know what this is. Note, sudo fdisk -l will list all the partitions available.

Retrieve your fstab and menu.lst and post here. Also post the output of sudo fdisk -l

---

