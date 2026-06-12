---
title: "Low disk space"
date: 2012-12-12
forum: General Help
---

### Post by Phoenix1941 on 2012-12-12
Hi, i am new to Ubuntu and i have this problem with free space when trying to update Ubuntu 12.04 i keep receiving this message:

"The upgrade needs a total of 5,243 k free space on disk '/tmp'. Please free at least an additional 4,223 k of disk space on '/tmp'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

taking into consideration that i have granted 10G of disk space upon the installation for Ubuntu of duo boot with win7 and that my disk configuration is as follow:


phoenix@ubuntu:~$ sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      9.4G  7.0G  2.0G  78% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           799M  952K  798M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  316K  2.0G   1% /run/shm
/dev/sda1       466G  206G  261G  45% /host
overflow        1.0M   28K  996K   3% /tmp
/dev/sdb2       465G  215G  250G  47% /media/My Toshiba

Appreciate your help.

Thanks in advance

---

### Post by Pjotr123 on 2012-12-12
Can you post a screenshot of a Gparted window? Much easier to analyze...

---

### Post by Impavidus on 2012-12-12
> **Phoenix1941 said:**
> 
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      9.4G  7.0G  2.0G  78% /
...
/dev/sda1       466G  206G  261G  45% /host

This sounds like a wubi install instead of a true dual boot. Am I correct?

---

### Post by arpanaut on 2012-12-12
If it is a Wubi install this is how you increase size: [https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

From: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Phoenix1941 on 2012-12-13
Yes, it is Wubi install, i have emptied some big files from the home folder and then increased the size of the virtual disk and its fine now :)

Thank you guys for your replies and assistance it is most helpful.

---

