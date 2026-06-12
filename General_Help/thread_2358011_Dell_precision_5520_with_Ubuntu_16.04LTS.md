---
title: "Dell precision 5520 with Ubuntu 16.04LTS"
date: 2017-04-08
forum: General Help
---

### Post by sofianito on 2017-04-08
Hi,


Few days ago I received my Dell Precision 5520. It came with a pre-installed ubuntu 16.04. The weird thing is that when booting the first time, I can only login as a guest user by pressing enter key. I can't sudo or do anything useful.


The disk has 3 partitions:
/dev/sda1 (EFI partition type - FAT32 - 524MB)


/dev/sda2 (Basic Data type - FAT32 - 3.2GB)


/dev/sda3 (Linux Filesystem Ext4)


I guess the second partition holds the recovery image, isn't it?


I am tempted to reinstall ubuntu on the third partition, but feel like I would be missing some specific dell drivers that wouldn't be present from the general ubuntu 16.04 distro?


What should I do?

---

### Post by RobGoss on 2017-04-08
Hello and welcome, Do to the fact you just bought this machine I won't reccommend doing anything to the OS, why don't you contact the manufacture and let them know what's going on with the login issue they should be able to assit you. I would think you have a warranty on it correct? they should be able to help or maybe even send you another machine

I'm sure you could just reinstall Ubuntu but it seems a waste of services on your part

---

### Post by sofianito on 2017-04-09
@RobGoss: Thanks for the tip

I finally managed to install ubuntu 16.04 LTS using the Dell rehcovery ISO I downloaded from Dell support site. I believe this is the proper way to do it.

Now I have installed it, I wish I could switch to Ubuntu Gnome instead of Unity ... There is no recovery image for Ubuntu Gnome. Is there a an easy way to do it?

---

### Post by howefield on 2017-04-09
> **sofianito said:**
> Now I have installed it, I wish I could switch to Ubuntu Gnome instead of Unity ... There is no recovery image for Ubuntu Gnome. Is there a an easy way to do it?

Probably best way would be to install from an Ubuntu Gnome live media in the same way that you installed "vanilla" Ubuntu. Bear in mind that if you need support from Dell you would probably need to restore back to factory default installation.

---

### Post by dragonfly41 on 2017-04-09
Alternatively, you can install gnome flashback (I use it in my Dell laptop to switch away from Unity).

[https://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/](https://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/)

---

### Post by RobGoss on 2017-04-09
>  I finally managed to install ubuntu 16.04 LTS using the Dell rehcovery ISO I downloaded from Dell support site. I believe this is the proper way to do it. 

Good choice I would take advantage of the support offered by Dell after all you payed for that

---

### Post by onoffpt2 on 2017-11-16
Would it be possible to make that Ubuntu ISO available somewhere?

---

