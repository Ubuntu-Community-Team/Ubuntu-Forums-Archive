---
title: "Dual boot installing grub unable to mount?"
date: 2008-03-03
forum: General Help
---

### Post by teryowen on 2008-03-03
I have recently reinstalled windows on my laptop which dual boots with ubuntu.

But when i try to reinstall grub, its gives me errors about being unable to mount.

i do this in teminal

sudo grub
root (hd0,4)
setup (hd0)
quit

the error comes after the setup (hd0) command. The drive which Ubuntu is on is sda5 (or the 4th partition on the first HD)

So the error says that it is unable to mount the drive

but when i go about mounting the drive manually to /mnt/sda5

by using
sudo mount /dev/sda5 /mnt/sda5
it works fine

Any ideas on what i can do to install grub?

Also im booting from an xubuntu live cd and this is for a Ubuntu 7.10 gg.

---

### Post by cconklin2376 on 2008-03-03
Try installing grub from a Knoppix live CD. 

Boot Knoppix. Mount your root partition read/write and create a /boot/grub/menu.lst file. You can copy the file from the Knoppix CD from /usr/share/doc/grub/examples/menu.lst.

or you can use the update-grub utility. It must be run from a chroot environment on the root patrition.

$ cd /mnt/sda5
$ sudo mkdir boot/grub
$ sudo cp /sbin/update-grub ./
$ sudo chroot /mnt/sda5 /update-grub

choose yes to create. 

open the menu.lst and change the # groot=(hd0,0) with your root device.

rerun update-grub:

$ cd /mnt/sda5
$ sudo chroot /mnt/sda5 /update-grub  

* this assumes that sda5 is your root partition

now install grub

sudo grub-install --root-directory=/mnt/hda1 /dev/hda
* change above hda and hda1 to reflect your root partition.

Good Luck!

---

### Post by teryowen on 2008-03-03
hey thanks for the reply.

I tried what you said it got me on the right track i just played around with it, and i ended up changing some partition numbers and it worked so it was all probably some stupid mistake where i had a wrong number.

---

