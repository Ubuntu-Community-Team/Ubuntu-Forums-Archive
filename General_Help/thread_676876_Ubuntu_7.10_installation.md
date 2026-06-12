---
title: "Ubuntu 7.10 installation"
date: 2008-01-24
forum: General Help
---

### Post by Sridhar_S1 on 2008-01-24
I have a system with Win XP Pro already installed on it in NTFS file format. I have 4 partitions. I installed Ubuntu. But it wiped out XP. While installing Ubuntu i chose the option "resize IDE master and use free space". 
i reinstalled XP. it wiped out Ubuntu. 
Can anyone guide me on how to install Ubuntu without wiping out XP?
a step by step explanation wud be really helful.

Thanks
Sridhar

---

### Post by forestpixie on 2008-01-24
first are you sure it deleted ubuntu - boot the livecd and see if it's in there, when you've booted the livecd run this from terminal

sudo fdisk -l

you can tell from that what partitions you have

windows installation will rewrite the boot record and lose ubuntu - you can reinstall grub - easiest way I found was to download and burn supergrub as an iso - boot with it and you can rewrite grub 
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Are you sure that your xp got deleted or just that you couldn't bott - the installer will only use the whole disc if you tell it to do so

---

### Post by amdalex on 2008-01-24
Make sure you are installing them on seoarate partitions only, don't let them mess with the other partitions on the drive. Also you need an extra partition for Ubuntu because of the swap. That way there is no way for any of them to have a conflict. If you install XP first and then install Ubuntu its likely that Grub will recognize your XP install.

---

