---
title: "where did my disk space go..."
date: 2007-02-24
forum: General Help
---

### Post by Polygon on 2007-02-24
today when i tried to start up ubuntu, i could not login because somehow my root partiton was 100% "full"

after uninstalling xubuntu-desktop, i finally could log back in

but i dont understand why its saying that it is full

here is the output of "df -h"

> mark@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/hde2             9.9G  9.3G   71M 100% /**
varrun                506M  108K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  172K  9.9M   2% /proc/bus/usb
udev                   10M  172K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/hde1             228M   20M  196M  10% /boot
/dev/hde4              25G   22G  1.6G  94% /home
/dev/hdf2              56G   52G  3.1G  95% /media/Programs
/dev/hdf3              45G   37G  8.4G  82% /media/WinData
/dev/hdf5              12G  7.2G  4.9G  60% /media/Windows
/dev/sda1             250G  165G   86G  66% /media/WinBackup
/dev/sda3              50G   12G   39G  23% /media/usbdisk
mark@ubuntu:~$ 


where did my .6 gigabytes go? And is there any suggestions on how to clean this out.... besides doing rm ~/trash/* and aptitude clean and all that stuff. I think its just time to get a bigger hard drive =P

---

### Post by nereid on 2007-02-24
Everything that you install and/or update will be saved on your harddisk, meaning you can find all *.deb files in /var/cache/apt/archives which can grow really big after some time.

---

### Post by tendays on 2007-02-24
The du (disk usage) command is useful to diagnose that kind of problems and see what takes up all that space. Try something like du -sxh /*
-s is to keep the output short
-x is to only look at the / partition
-h is to have it use the KB MB GB notation
/* is to instruct it to show you space taken up by each sub directory of / separately. Then run the command again on the directory you see is taking up the place. E.g. du -sxh /var/*

HTH

---

