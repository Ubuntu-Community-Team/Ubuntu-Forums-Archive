---
title: "mount won't mount entire partition- stupid superuser"
date: 2006-10-16
forum: General Help
---

### Post by m2006h on 2006-10-16
I'm stuck on this one. When I mount /dev/hda2, which is 15G, I can only see 5G (apparently). Below is the printout from fdisk showing /dev/hda2, and a df of my running system showing only 5G of /dev/hda2 mounted.

What am I doing wrong?

mike



Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         510     4096543+   b  W95 FAT32
/dev/hda2             511        2434    15454530   83  Linux

Command (m for help): q


xxxx@xxx:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb1             23928032  13824404  10103628  58% /
varrun                  257504        92    257412   1% /var/run
varlock                 257504         4    257500   1% /var/lock
udev                    257504       384    257120   1% /dev
devshm                  257504         0    257504   0% /dev/shm
lrm                     257504     18316    239188   8% /lib/modules/2.6.15-27-686/volatile
/dev/hdb2              4883556   3953628    929928  81% /home
/dev/hdd               8065054   8065054         0 100% /media/cdrom0
/dev/hda2              5124508     32840   5091668   1% /media/data

---

### Post by m2006h on 2006-10-16
sorry to reply to my own thread. like I said, stupid superuser.

I reformatted the /dev/hda2 partition using mkfs and now the entire partition mounts as expected.

sorry for the noise

---

