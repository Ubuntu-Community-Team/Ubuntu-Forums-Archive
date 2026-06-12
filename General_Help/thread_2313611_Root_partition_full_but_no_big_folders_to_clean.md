---
title: "Root partition full but no big folders to clean"
date: 2016-02-14
forum: General Help
---

### Post by jeanjan2 on 2016-02-14
Hi,

The root partition is almost full but I don't see any big files or folders to clean.
```
root@ux1:/# df -hSys. de fichiers Taille Utilisé Dispo Uti% Monté sur
/dev/root           20G     18G  478M  98% /
devtmpfs           3,9G    4,0K  3,9G   1% /dev
none               4,0K       0  4,0K   0% /sys/fs/cgroup
none               788M    564K  787M   1% /run
none               5,0M       0  5,0M   0% /run/lock
none               3,9G       0  3,9G   0% /run/shm
none               100M       0  100M   0% /run/user
/dev/sda3          1,8T    633G  1,1T  37% /home
root@ux1:/#
```
```
root@ux1:/# du -sk * | sort -n
du: impossible d'accéder à «proc/28376/task/28376/fd/4»: Aucun fichier ou dossier de ce type
du: impossible d'accéder à «proc/28376/task/28376/fdinfo/4»: Aucun fichier ou dossier de ce type
du: impossible d'accéder à «proc/28376/fd/4»: Aucun fichier ou dossier de ce type
du: impossible d'accéder à «proc/28376/fdinfo/4»: Aucun fichier ou dossier de ce type
du: impossible d'accéder à «proc/28380»: Aucun fichier ou dossier de ce type
0    proc
0    sys
4    dev
4    lib64
4    mnt
4    opt
4    srv
8    media
16    lost+found
56    root
564    run
5236    etc
9804    bin
18540    boot
25012    sbin
29524    lib
102108    tmp
551544    usr
552952    var
663396332    home
root@ux1:/#
```
```
root@ux1:/# ls -al
total 92
drwxr-xr-x  22 root root  4096 févr. 11 13:13 .
drwxr-xr-x  22 root root  4096 févr. 11 13:13 ..
drwxr-xr-x   2 root root  4096 févr. 14 11:56 bin
drwxr-xr-x   3 root root  4096 nov.  27 10:10 boot
drwxr-xr-x  14 root root 14160 déc.   1 22:17 dev
drwxr-xr-x  97 root root  4096 févr. 14 11:56 etc
drwxr-xr-x   4 root root  4096 nov.  27 10:19 home
drwxr-xr-x  17 root root  4096 juil. 23  2014 lib
drwxr-xr-x   2 root root  4096 mars  24  2015 lib64
drwx------   2 root root 16384 nov.  27 10:09 lost+found
drwxr-xr-x   3 root root  4096 avril 15  2014 media
drwxr-xr-x   2 root root  4096 févr. 27  2014 mnt
drwxr-xr-x   2 root root  4096 mars  26  2014 opt
dr-xr-xr-x 181 root root     0 déc.   1 22:17 proc
drwx------   4 root root  4096 nov.  30 14:33 root
drwxr-xr-x  16 root root   660 févr. 14 12:16 run
drwxr-xr-x   2 root root 12288 févr. 14 11:56 sbin
drwxr-xr-x   2 root root  4096 mars  26  2014 srv
dr-xr-xr-x  11 root root     0 févr. 11 13:12 sys
drwxrwxrwt   2 root root  4096 févr. 14 12:16 tmp
drwxr-xr-x  10 root root  4096 avril 15  2014 usr
drwxr-xr-x  13 root root  4096 avril 16  2014 var
root@ux1:/#
```

Are there any hidden files somewhere hidden?

---

### Post by blueridgedog on 2016-02-14
Anything in /root/.local/share/Trash/ ?

---

### Post by jeanjan2 on 2016-02-14
There's no [COLOR=#000000]/root/.local/share/Trash/ folder.[/COLOR]

```
root@ux1:/# cd /root/
root@ux1:~# ls -al
total 56
drwx------  4 root root 4096 nov.  30 14:33 .
drwxr-xr-x 22 root root 4096 févr. 11 13:13 ..
-rw-------  1 root root 8983 févr. 11 15:37 .bash_history
-rw-r--r--  1 root root 3106 févr. 20  2014 .bashrc
drwx------  2 root root 4096 nov.  27 10:13 .cache
-rw-r--r--  1 root root   25 nov.  27 10:13 .email
-rw-r--r--  1 root root    7 nov.  27 10:13 .mdg
-rw-------  1 root root   90 févr. 11 13:25 .nano_history
-rw-r--r--  1 root root  316 nov.  27 10:10 .ovhrc
-rw-r--r--  1 root root  140 févr. 20  2014 .profile
-rw-r--r--  1 root root   66 nov.  30 14:33 .selected_editor
drwxr-xr-x  2 root root 4096 janv. 20 15:04 .ssh
root@ux1:~#
```

It's a server install.

---

### Post by spjackson on 2016-02-14
The result of du comes to around 13GB which is significantly less than 18GB shown by df. Perhaps you have some files or folders in / that do not match * (i.e. beginning with a period). If a file has been deleted but is still open then the space is not recovered; a reboot is one way to clear that.

Of the 13GB that is showing, 1GB in /tmp seems excessive, unless you know of a good reason for it. Also 5.5 GB in /var - is this mainly /var/log? Do you have very old logs you don't need?

---

### Post by jeanjan2 on 2016-02-14
It was way less than that.

```
root@ux1:/# du -sh * | sort -h
du: impossible d'accéder à «proc/22822/task/22822/fd/4»: Aucun fichier ou dossier de ce type
du: impossible d'accéder à «proc/22822/task/22822/fdinfo/4»: Aucun fichier ou dossier de ce type
du: impossible d'accéder à «proc/22822/fd/4»: Aucun fichier ou dossier de ce type
du: impossible d'accéder à «proc/22822/fdinfo/4»: Aucun fichier ou dossier de ce type
0    proc
0    sys
4,0K    dev
4,0K    lib64
4,0K    mnt
4,0K    opt
4,0K    srv
8,0K    media
16K    lost+found
56K    root
564K    run
5,2M    etc
9,6M    bin
19M    boot
25M    sbin
29M    lib
104M    tmp
539M    usr
542M    var
640G    home
root@ux1:/#
```

Thank you for submitting the idea of deleted open files.

I did that :
```
root@ux1:/# lsof -nP +L1
COMMAND     PID   USER   FD   TYPE DEVICE    SIZE/OFF NLINK     NODE NAME
cron       1496   root    5u   REG    8,2 17587380699     0   391972 /tmp/tmpfZif7fG (deleted)
updatemet  1497 root    1u   REG    8,2 17587380699     0   391972 /tmp/tmpfZif7fG (deleted)
updatemet  1497 root    2u   REG    8,2 17587380699     0   391972 /tmp/tmpfZif7fG (deleted)
root@ux1:/#
```
I killed the "updatemet" process and restarted cron.
And now :
```
root@ux1:/# df -h
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
/dev/root           20G    1,3G   17G   8% /
devtmpfs           3,9G    4,0K  3,9G   1% /dev
none               4,0K       0  4,0K   0% /sys/fs/cgroup
none               788M    564K  787M   1% /run
none               5,0M       0  5,0M   0% /run/lock
none               3,9G       0  3,9G   0% /run/shm
none               100M       0  100M   0% /run/user
/dev/sda3          1,8T    640G  1,1T  38% /home
root@ux1:/#
```

Thank you all.

---

