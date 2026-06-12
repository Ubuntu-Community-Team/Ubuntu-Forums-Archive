---
title: "Grub Rescue Prompt After Deleting Partition"
date: 2016-06-08
forum: General Help
---

### Post by lava2 on 2016-06-08
I have two HDDs in my laptop:

HDD1: Two partitions; an Ubuntu 14.04 install and another storage partition (my pics, files, etc). 
HDD2: A second Ubuntu 14.04 install.  

Both Ubuntu OS's showed up in GRUB just fine until, using a bootable Ubuntu USB stick, I deleted the the Ubuntu install on HDD1 and added that space to the storage partition. 
That was not the right thing to do, huh? Now I get a GRUB Rescue prompt when I turn on my laptop. 

So now I have the following:

HDD1: Storage
HDD2: Ubuntu

How can I go in and fix GRUB so that I can boot to HDD2? Can I use the bootable Ubuntu USB stick to do it?

Thanks!

---

### Post by ventrical on 2016-06-08
Using the bootable USB stick to do this has not worked for me. What has worked is Grub Rescue bootable CD. It most never fails to recover from a fault like this.

Regards..

---

### Post by grahammechanical on 2016-06-08
The version of Ubuntu on HDD1 was in control of the boot menu (Grub). Which looks for its configuration files in /boot/grub/ on the Ubuntu partition. By deleting that partition you deleted the grub configuration files. Grub, itself, is still installed on HHD1 but it cannot find its configuration files.

Now we find out if you are a lucky person. When you installed Ubuntu on HDD2 did you direct the installer to install Grub on HDD2? Or did you let it install Grub on HDD1? The default setting is sda (the first hard disk) but you are not using the terms sda & sdb to refer to the first or second hard disk.

If Grub is installed on HDD2 then you can enter the BIOS/UEFI setting utility and change the setting to load from HDD2 and if that loads Ubuntu then run

```
sudo update-grub
```

If you are out of luck then you need to find out if what you call HDD2 is what Linux calls sda or if it is sdb. If you know which it is then you can run a live session. Then use the file manager to open the Ubuntu partition on HDD2 and then in a terminal run

```
sudo update-grub
sudo grub-install /dev/sda
```

or 

```
sudo update-grub
sudo grub-install /dev/sdb
```

It matters whether HDD2 is sda or sdb. I am not sure if the "sudo" prefix is needed when doing this from a terminal in a live session. It is years since I need to do this.

Regards.

---

