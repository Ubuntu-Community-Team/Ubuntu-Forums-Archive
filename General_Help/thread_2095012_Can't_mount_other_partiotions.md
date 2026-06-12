---
title: "Can't mount other partiotions"
date: 2012-12-15
forum: General Help
---

### Post by marticc on 2012-12-15
Hi,

I've got a problem I hope you can help me to solve.

I 've got a laptop with three OS;

Ubuntu 12.04 (with a parition for /, and another for /home)
Windows 7
Debian Testing (I have installed it in a LVM, with 4 partitions /boot (non encrypted), and swap,  /home and / (all of them encrypted).

The problem, is that I can not mount/see/find my Debian partition when I am using Ubuntu (I type the right passphrase but the volume where Debian is located is not mounted). The consequence of all this is that if I start my laptop using the "ubuntu grub" I can't see my Debian partition in the grub menu.

That is not a big problem because I use the "Debian grub" to start the laptop (and with that grub I can see Debian, ubuntu and windows). However, as the laptop uses the latest grub installed, everytime Ubuntu releases an update for grub, after updating it, my laptop starts with the "ubuntu grub", and I need the supergrub disk to start my debian partition and reinstall "Debian grub" (so that the next time I start my laptop it uses "Debian grub"). To sum up, this grub issue is not a serious issue, but it  really is a  pain in the ****

I thought about uninstalling my Ubuntu grub, but everytime a new kernel for ubuntu is released I will have to install "ubuntu grub" again.

I guess that if I manage to mount the Debian partition while I am using ubuntu, and once debian is mounted I run update-grub, this issue would be fixed. So, my question is: Do you know how to get ubuntu to mount encrypted LVM?.


Thanks.

PS: Sorry for my poor English, I hope you understand my problem

---

### Post by Rexilion on 2012-12-15
A few points:

I better alternative to this would be to use a 'superGRUB' installation that is not owned by *any* distro (incl. Windows 7). This GRUB chainloads the other bootloaders:
- Windows 7
- Ubuntu
- Debian

That is a onetime setup. Any updates to the other bootloaders will not adversely affect your 'superGRUB' installation.

You have to choose to install your distro specific GRUB's MBR on the start of the partition, not on the start of the disk.

Is that a viable alternative? Get's you the best of both worlds without the hassle.


> The problem, is that I can not mount/see/find my Debian partition when I am using Ubuntu (I type the right passphrase but the volume where Debian is located is not mounted). The consequence of all this is that if I start my laptop using the "ubuntu grub" I can't see my Debian partition in the grub menu.

That could be a bug. How do you attempt to do this? Through the GUI? Or the commandline?

---

### Post by oldfred on 2012-12-15
I do not think the lvm drivers are included by default. Install them and mount Debian. Then rerun grub udate.

#From Ubuntu
       sudo apt-get install lvm2
    # mount Debian lvm

sudo update-grub

---

### Post by marticc on 2012-12-15
Oldfred you were right, lvm is not installed by default, and after installing it I can mount my encrypted debian. thanks!

Rexilion, you said: "I better alternative to this would be to use a 'superGRUB' installation that is not owned by *any* distro...You have to choose to install your distro specific GRUB's MBR on the start of the partition, not on the start of the disk". That looks a great idea, I will look for that option next time start my laptop. Thanks for your answer

---

