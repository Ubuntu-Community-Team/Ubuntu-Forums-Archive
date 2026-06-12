---
title: "Running Ubuntu 6.06 from External HDD"
date: 2007-08-18
forum: General Help
---

### Post by tmbflyer on 2007-08-18
I would like to run ubuntu off my external 40GB HDD so that I can easily swich between windows and ubuntu without opening the case on my Compaq Presario Laptop. I put the drive into the laptop to install ubuntu, but it will not boot when it is hooked up with USB adapter. The boot up fails at mounting root file system.
I get the error "/bin/sh: can't access tty; job control turned off"
Thanks for any help

---

### Post by confused57 on 2007-08-18
> **tmbflyer said:**
> I would like to run ubuntu off my external 40GB HDD so that I can easily swich between windows and ubuntu without opening the case on my Compaq Presario Laptop. I put the drive into the laptop to install ubuntu, but it will not boot when it is hooked up with USB adapter. The boot up fails at mounting root file system.
I get the error "/bin/sh: can't access tty; job control turned off"
Thanks for any help
Boot up the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Also mount your Ubuntu root partition from the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Once you've mounted your root partition, post the output of your /etc/fstab and /boot/grub/menu.lst.
I'm guessing that your external hard drive designation(hda,hdb,etc) changed when you reconnected your drive as an external device.

---

