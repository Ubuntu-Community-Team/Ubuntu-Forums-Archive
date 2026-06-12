---
title: "keeping same grub although installing new distros"
date: 2012-11-05
forum: General Help
---

### Post by deserthowler on 2012-11-05
I have searched for information on this subject but apparently haven't chosen the right search terms.  :(

I run Ubuntu 12.04 and am OK with it.  Although I stick with Ubuntu, I like to install and check other distros on separate partitions.  When I install another distro, its grub takes over.  I would like to contimue using grub from Ubuntu 12.04 no matter what other distro I install.  Are there any suggestions?

I am not interested in running Vbox.  I don't feel I have enough memory (2GB) to do this. I also feel I don't need another layer of confusion to the situation.

Earl

---

### Post by oldfred on 2012-11-05
I have multiple drives, so if I install something else I let it overwrite the boot loader in sda, but keep BIOS on sdc. You could do something similar with a flash drive that has the boot loader you always want. 

Most installs give a choice on where to install the boot loader. And most installs will find other installs and let you boot them. But not always.

Best to have Ubuntu liveCD, Boot-Repair and other repair tools.

If you end up with another install's boot loader and you can still boot into Ubuntu, run this from Ubuntu to restore its boot loader.

sudo grub-install /dev/sda
sudo update-grub

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
My flash was labeled MC4GB and mounted to media/fred and is sdb.
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

---

### Post by Zimmer on 2012-11-05
When you install another distro make sure at install that you DO NOT install grub to the boot partition, but to the installation partition instead (even that may be unnecessary ). There will be an option for this during install, usually around the time the installer asks for partition info.
When installed, boot your 12.04 and in a Terminal,

sudo update-grub

This will update GRUB and find your new install and add it to the GRUB menu, leaving your main install as the first option.

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
is an old resource I found useful for GRUB.

---

### Post by deserthowler on 2012-11-05
> **oldfred said:**
> 

```
sudo grub-install /dev/sda
sudo update-grub
```



This worked just great!!!  I have been looking at that problem for a VERY long time.  Such a simple solution.

Earl

---

