---
title: "Boot up 7+ minutes, with 16gb ram, SSD, and Core i7"
date: 2014-06-04
forum: General Help
---

### Post by MSklaroff on 2014-06-04
Decided to give Lubuntu 14.04 a shot. Used UNetbootin to make a bootable USB key with Lubuntu ISO. Formated hard disk and Installed sucessfuly. 

Booting up takes 7 minutes plus, entire computer is generally sluf=ggish even with delays between when I type keys and when I see them. Programs take forever to start up. SHould not happen on a  Dell Studio XPS with i7, 16gb ram, and SSD. Without firefox running, CPU is about 5% with only 494 MB memory used.

I am just zipping my entire var/log directory and uploading it to see if anyone can make sense of it. I don't know where to look in the logs to begin with. I'll give you guys  everything.

---

### Post by oldfred on 2014-06-05
First look at dmesg for any failure, error that keeps trying & then fails (or succeeds after many tries) or entries with long time stamps between them. That should indicate where to check for corrections.

gksudo gedit /var/log/dmesg

Seems to want to run fsck?
[    6.058132] EXT4-fs (sda1): INFO: recovery required on readonly filesystem

Are you using bluetooth & IPv6? Could save a few seconds.

Note Intel setting required in XPS15, they say it applies to all Intel based systems.
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

Some with Intel are finding the very new kernels have fixes. But you have to use a ppa to install them.
      
 New kernels ppa
xorg-edgers PPA
Oibaf PPA discusion  [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
Linux 3.15 Git kernel from the Ubuntu Mainline Kernel PPA while the Oibaf PPA was also loaded for the Mesa 10.3-devel Git master snapshot and xf86-video-ati 7.3.99 Git.

---

