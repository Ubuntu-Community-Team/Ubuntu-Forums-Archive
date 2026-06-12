---
title: "why free spaces no change after i delete some files"
date: 2007-02-27
forum: General Help
---

### Post by helai on 2007-02-27
when I have installed ubuntu on hdb8,and backup the whole partition by using a4l(the backup software) to the hdb8,after that i found the backup is too larger as 8g ,so delete it and empty it from trashmbut try to check the free spaces on hdb8,found it is no change,see below message

lenovo@lenovo-desktop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on

/dev/hdb8     ext3    9.9G  8.9G  586M  94% /

varrun       tmpfs    506M   76K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
procbususb   usbfs     10M  148K  9.9M   2% /proc/bus/usb
udev         tmpfs     10M  148K  9.9M   2% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M  8.0M  498M   2% /lib/modules/2.6.17-11-generic/volatile
/dev/hdb7     ext3    7.4G  170M  6.8G   3% /home
/dev/hda9     ntfs     89G   68G   22G  77% /media/hda9
/dev/hdb1     ntfs    9.4G  7.0G  2.4G  76% /media/hdb5

and on qtparted,i can't find the used space on hdb6,and the sequence of the partition is different with the result comes from ~$ df -Th. what's wrong about it
see the picture

---

