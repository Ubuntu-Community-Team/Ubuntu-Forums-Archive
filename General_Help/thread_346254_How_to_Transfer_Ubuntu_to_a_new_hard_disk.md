---
title: "How to Transfer Ubuntu to a new hard disk"
date: 2007-01-25
forum: General Help
---

### Post by tknee on 2007-01-25
HI

I am planning on installing a new IDE hard disk in my DELL computer. Is there a simple way to transfer the entire UBUNTU operating system, programs, users, configuration to the new drive.

I am currently operating a dual boot system with XP and GRUB and would like to maintain the same. I know in Windows XP I can just make a Ghost image with Norton and life becomes very simple.

Thanks

---

### Post by kosmic on 2007-01-25
There is a lot of ways to acomplish that. you can use a program like ***partimage*** just search for it in synaptic or you can use the **dd** command :)

here -> [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) you have a tutorial about partimage

---

### Post by Irony on 2007-01-25
Use this method;

[http://www.pclinuxos.com/forum/index.php?topic=13404.0](http://www.pclinuxos.com/forum/index.php?topic=13404.0)

---

### Post by bodhi.zazen on 2007-01-25
Or you can use gparted, either from the Ubuntu live CD or from the Gparted CD.

Regardless of how you copy/move the partition:

1. I advise you move/copy the partition from a live CD.

2. After the move, however, you will need to update /boot/grub/menu.lst and /etc/fstab to the new location/partition. Do this from the live CD before you reboot.

---

