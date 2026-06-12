---
title: "Unable to mount new external hard drive"
date: 2020-08-26
forum: General Help
---

### Post by chippermon on 2020-08-26
I have a new Seagate Backup Plus Portable Hard Drive. I am trying to back up my Lubuntu desktop onto it but the computer won't mount it. It recognizes it in the tree. I right click and try to mount but it still won't. 

This is the error message I get when I first connect it.

"Error mounting /dev/sdb2 at /media/chip/Backup Plus: unknown filesystem type 'exfat' "

I just finished backing up my laptop that runs Mageia 7 on this portable hard drive without issue ( I know it is a fork from Mandriva) but I know the drive is fine. Maybe just the wrong file system for Debian? Maybe I'm missing something. Does anyone have a suggestion?

The machine is running Ubuntu 18.04.5 LTS

Kernel 4.15.0-112

Thanks for your help

---

### Post by VMC on 2020-08-26
With the drive inserted, what does the output of this show?
```
lsblk -f
```

---

### Post by oldfred on 2020-08-26
Not exactly sure which exFAT Ubuntu has in 20.04.1 as it said it has updated it. So maybe they backported the newer driver.

Microsoft patent restricted exFAT, so it had to be reverse engineered. The have opened that up and a newer update to driver will be available, but probably not in older versions.

The New Microsoft exFAT File-System Driver Is Set To Land With Linux 5.7
[https://www.phoronix.com/scan.php?page=news_item&px=New-exFAT-For-Linux-5.7](https://www.phoronix.com/scan.php?page=news_item&px=New-exFAT-For-Linux-5.7)
[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)
For 13.10 & later for older driver
sudo apt-get update && sudo apt-get install exfat-utils

If backing up Linux files, you do not want to use Windows formats. They do not support Linux ownership & permissions, so trying to restore any data loses those. If just your data files, it is usually possible to reset owership & permissions, but you cannot reset system as there are multiple required owners & permissions.

Example of users:
```
fred@z97-focal-kubuntu:~$ id
uid=1000(fred) gid=1000(fred) groups=1000(fred),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),121(lpadmin),131(lxd),132(sambashare)


```

---

### Post by chippermon on 2020-08-26
chip@chip-Inspiron-530s:~$ lsblk -f
NAME   FSTYPE LABEL       UUID                                 MOUNTPOINT
sda                                                            
&#9500;&#9472;sda1 ext4               6bdc53dc-3088-4753-829c-f67d08e4f56a /
&#9500;&#9472;sda2                                                         
&#9492;&#9472;sda5 swap               7e5a2aaa-c40a-4870-948b-01df7f181c05 [SWAP]
sdb                                                            
&#9500;&#9472;sdb1 vfat   EFI         67E3-17ED                            
&#9492;&#9472;sdb2 exfat  Backup Plus 5F19-4A1E                            
sr0

---

### Post by VMC on 2020-08-26
I found this article that sounds like your issue:
[https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/](https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/)

---

### Post by chippermon on 2020-08-26
> **VMC said:**
> I found this article that sounds like your issue:
[https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/](https://www.howtogeek.com/235655/how-to-mount-and-use-an-exfat-drive-on-linux/)

Wow! That did it. Thank yo so much.:D

---

