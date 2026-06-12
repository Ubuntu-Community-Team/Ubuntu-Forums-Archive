---
title: "Moved boot partition - make new UUID? in LiveUSB now"
date: 2013-02-16
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-02-16
Everybody asleep? In LiveUSB mode, using GParted,

/sda3 has expanded to absorb all of former /sda1.

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3e1e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3   *        2048   174176255    87087104   83  Linux
/dev/sda4       174176791   781417664   303620437    5  Extended
/dev/sda5       174176793   764420894   295122051   83  Linux
/dev/sda6       764420958   781417664     8498353+  82  Linux swap / Solaris

ubuntu@ubuntu:/$ sudo mkdir /media/newpart
ubuntu@ubuntu:/$ cd /media
ubuntu@ubuntu:/media$ ls
cdrom  newpart
ubuntu@ubuntu:/media$ cd /
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda1 /media/newpart -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
**mount: special device /dev/sda1 does not exist**

I know I have to get a new UUID, but I had the impression that GParted would probived (generate) a new UUID once the "move/resize? was completed.

What's more: do I edit my /etc/fstab now, and the sudo update grub or vice-versa?

---

### Post by dino99 on 2013-02-16
you are right, every resizing/tweaking of the partition(s) create a new uuid.
Meaning  to catch the change made, you need then to run: sudo update-grub .
There is no need to tweak fstab, the mountall package automatically deal "on the fly" with the mount/umount settings.  :p

---

### Post by Mark_in_Hollywood on 2013-02-16
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

netsearching around, I found: 
[URL="http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd/#.UR9GuM8ghoA"]
How to Repair, Restore, or Reinstall Grub 2 with a Ubuntu Live CD[/URL]

ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# grub-install --recheck /dev/sda
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
done

. . . A few moments later, upon reboot into "new" /sda3, created by above grub install and grub re-check commands, my system if perfect. WOW!

Post closed, thanks again.

---

