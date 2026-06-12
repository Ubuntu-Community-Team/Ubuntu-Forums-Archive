---
title: "Help with Adding Partitions to GRUB"
date: 2008-05-18
forum: General Help
---

### Post by speedemonspecv on 2008-05-18
So I've got my Vista/Hardy dual-boot working fine, but I wanted a bit more. I installed a hacked version of OS X Leopard onto another partition, and got that working fine. But I'm trying to add that partition as an entry to GRUB, but it is not complying. Here is the output to "sudo fdisk -l":

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde6cde6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1285       17828   132889680    7  HPFS/NTFS
/dev/sda2           17829       19457    13084942+   5  Extended
/dev/sda3               1        1284    10313698+  83  Linux
/dev/sda5           17829       19382    12482473+  83  Linux
/dev/sda6           19383       19457      602406   82  Linux swap / Solaris

```

Now, I know /dev/sda3 is the partition with Leopard on it, but I can't figure out what number to put into /boot/grub/menu.lst to get it to boot correctly. I tried "(hd0,3)" and "(hd0,5)" but neither worked. I would appreciate any help with this.

---

### Post by MDSmith2 on 2008-05-18
Try to run sudo update-grub
That should do it automatically .

---

### Post by speedemonspecv on 2008-05-18
sudo update-grub didn't help.

---

### Post by meierfra. on 2008-05-18
I know nothing about booting Leopard, but /dev/sda3 is (hd0,2) in Grub speak.

---

### Post by speedemonspecv on 2008-05-19
Ok, that pointed GRUB to the right partition, but now I'm getting HFS+ errors from Leopard. I guess its because I shrunk and then moved the partition to a different drive. But that's not an Ubuntu problem, now is it? :) Thanks for your help, guys.

---

