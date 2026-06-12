---
title: "grub lost, won't reinstall"
date: 2007-02-16
forum: General Help
---

### Post by mvaniersel on 2007-02-16
I used gparted to change my partitions around a bit. When rebooting, I got the feared "grub error 15". I booted the live CD again and I'm trying to restore grub. My filesystem root is at /dev/sda6 so here is what I tried:

sudo -i
mkdir /mnt/ubuntu
mount /mnt/ubuntu /dev/sda6
chroot ubuntu
grub

and then I got the following errors when trying to reinstall grub

grub> root (hd0,5)
Error 21: Selected disk does not exist
grub> find /boot/grub/stage1
Error 15: File not found

What is wrong? Why won't grub reinstall? /boot/grub/stage1 is right there on /dev/sda6!

---

### Post by mvaniersel on 2007-02-16
I managed to solve the problem by myself. Here is what I did:


```
sudo -i
cd /
mount -t ext3   /dev/sda6 /mnt 
mount -t proc   proc      /mnt/proc
mount -t sysfs  sys       /mnt/sys
mount -o bind   /dev      /mnt/dev
 
chroot /mnt /bin/bash

grub
root (hd0,5)
setup (hd0,5)
```

after that I could boot again into my windows partition. I still needed to edit /boot/grub/menu.lst and /etc/fstab to get ubuntu running, but that was easily done.

In short, the extra step needed was that I needed to mount the proc, sys and dev filesystems to get it working. What I don't understand is why most grub howtos don't mention this?

---

### Post by mc2003 on 2007-02-16
I dont know ho much this thread will help u [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by mvaniersel on 2007-02-16
Yeah, I tried that too at first, but it doesn't work. That is for dapper and before. For edgy it doesn't work anymore, because the installer on the live cd won't let you mount a / partition without formatting it. That howto is out of date.

---

