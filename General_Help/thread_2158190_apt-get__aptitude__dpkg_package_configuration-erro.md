---
title: "apt-get / aptitude / dpkg package configuration-error"
date: 2013-06-28
forum: General Help
---

### Post by truse on 2013-06-28
Hi,

Some weeks ago I activated Raring-proposed repo and did a "aptitude update && aptitude safe-upgrade" . In the middle of the upgrade process my computer froze and I had to do a hard reboot. 

Ever since then I keep getting the following error when installing or upgrading packages (more in attached txt):

$ sudo aptitude safe-upgrade 
```
 
The following partially installed packages will be configured:
  linux-generic linux-image-3.8.0-26-generic linux-image-extra-3.8.0-26-generic linux-image-generic 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up linux-image-3.8.0-26-generic (3.8.0-26.38) ...
Internal Error: Could not find image (/boot/vmlinuz-3.8.0-26-generic)
dpkg: error processing linux-image-3.8.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-26-generic:
 linux-image-extra-3.8.0-26-generic depends on linux-image-3.8.0-26-generic; however:
  Package linux-image-3.8.0-26-generic is not configured yet.
```

**See attachment for more output.**


So the problem seems to be the configuring of the packages ** linux-generic** **linux-image-3.8.0-26-generic** **linux-image-extra-3.8.0-26-generic** and **linux-image-generic**

The following commands have been executed without any luck:

```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```


I would very much like to get this problem sorted out. Anyone have any suggestions on how to solve this?

Thanks in advance.



**EDIT:** added some system info

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"

$ uname -a
Linux padda 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Hardware: Lenvo x230

---

### Post by dino99 on 2013-06-28
boot in recovery mode, then select network activation, then "dpkg" to repair the system; finally select "resume" to continue booting

---

### Post by truse on 2013-06-28
Thanks for answering so quickly.

However, Im having a bit of trouble booting into recovery mode. As this is a LVM encrypted disk i only see the disk-unlock screen and then im at gnome login screen. Do you have any tips&tricks?

I can boot into a live CD/USB and mount encrypted LVM if that helps with anything - but i dont know if im going to find the network activation and dpkg that you mentioned.

---

### Post by NGRhodes on 2013-07-11
Hi, do you have enough disk space left, in particular the paritition where /boot is located (and could be cause of kernel update failure).

Cheers, Nick.

---

### Post by truse on 2013-07-11
> **NickGRhodes said:**
> Hi, do you have enough disk space left, in particular the paritition where /boot is located (and could be cause of kernel update failure).

Cheers, Nick.

Hi, Nick.

Yes, I have. That was one of my first thoughts as well. 

```
/dev/sda1                    228M   94M  122M  44% /boot
```

Any other suggestions of what could be causing this?

---

