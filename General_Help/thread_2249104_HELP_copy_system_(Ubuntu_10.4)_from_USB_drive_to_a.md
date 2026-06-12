---
title: "HELP: copy system (Ubuntu 10.4) from USB drive to another usb drive"
date: 2014-10-19
forum: General Help
---

### Post by w1av on 2014-10-19
Hello,

I have a Ubuntu 10.4 installation on a 4 Gigabyte usb flash drive. It has persistent drive setting. Works great but I want to COPY the installation with all my saved data to a NEW and BIGGER usb drive (a 32 gigabyte). What is the procedure to  put the same data from my small drive to the new bigger drive?  I also want to INCREASE the size of my persistent drive setting.

---

### Post by O9aIevckc0 on 2014-10-19
desktop Ubuntu 10.4 is no longer supported as of 2013-05-09(no security updates and no new software). 
I strongly suggest  you make a backup of any important files and install a newer version
such as Ubuntu 14.04 supported until 2019-04

---

### Post by w1av on 2014-10-19
I tried that but 14.4 runs so slow it is unusable.  10.4 is the only version I can use on this machine for some reason. I have 4G ram so I dont understand why higher versions run too sluggish to be of use. Maybe there is a LIGHTER version of 14.4 that uses less resources for older computer?

---

### Post by yancek on 2014-10-19
It's probably not a good idea to still be running an outdated and unsupported system, either 12.04 or 14.04 are still supported.  You might be able to use dd to copy one flash drive to another such as in the command below.  That is if the 4GB shows as sdb and the 32GB shows as sdc.  You will need to verifywhat your drive names are on your machine.

```
dd if=/dev/sdb of=/dev/sdc
``` 

If you have one partition on your 4GB, you could create a partition on the new drive of equal or larger size and copy there.  This will not get you the bootloader so you would have to install grub to the mbr of the new flash and probably modify the grub.cfg file or files in /etc/grub.d and possibly your /etc/fstab file.

What format is the 4GB?  If it is FAT32 as is customary, you cannot create a persistent file larger than 4GB on the new flash.  You could create an additional partition of whatever size you want if you format it ext3, ext3.  If you reformat your current partition with the persistent file, you lose all your data.

I don't know if upgrading to 12.04/14.04 is a possibility for you.

[http://askubuntu.com/questions/110477/how-do-i-upgrade-to-a-newer-version-of-ubuntu](http://askubuntu.com/questions/110477/how-do-i-upgrade-to-a-newer-version-of-ubuntu)

---

### Post by O9aIevckc0 on 2014-10-19
if you need a lighter version you could try lubuntu 14.04 a light weight version of ubuntu 

[http://lubuntu.net/](http://lubuntu.net/)

---

