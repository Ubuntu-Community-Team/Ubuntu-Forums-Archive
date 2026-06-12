---
title: "Configuring(?) GRUB Question"
date: 2007-07-08
forum: General Help
---

### Post by drafael on 2007-07-08
I started out installing ubuntu with a 10GB partition. I have today decided that's not enough, as I'm going to switch over to ubuntu completely, with the dual boot to windows only for games etc.

Anyway, so I edited the partitioning using my livecd. What I did was shrink the windows partition further, and then copy the ubuntu partition so it's just after the windows partition, which will allow me to expand it - though I haven't done this yet. I then deleted the original ubuntu partition.

What this amounts to is my ubuntu install being on /dev/sda3, as opposed to /dev/sda2, which is what the GRUB bootloader points to. How do I change it so that it'll point to /dev/sda3, and so boot ubuntu properly?

Thanks in advance for any help ^^

---

### Post by drafael on 2007-07-08
Resolved.

What I did:
sudo mkdir /mnt/tmp && sudo mount -t ext3 /dev/sda3 /mnt/tmp
sudo gedit /mnt/tmp/boot/grub/menu.lst

Change all (0,1) to (0,2), save, reboot and it's going well (though on bootup, filesystem got fixed apparently).

Thanks to the people on #ubuntu who helped with this

---

