---
title: "[SOLVED] DVD drives not seen"
date: 2008-04-05
forum: General Help
---

### Post by sumithar on 2008-04-05
Using Ubuntu 7.10
Problem is I can't see my 2 DVD drives on the desktop anymore.  I never used to have to mount them or anything like that in the past.

Here is what I see when I run "df" command
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              6578112   2642200   3601760  43% /
varrun                  355256        88    355168   1% /var/run
varlock                 355256         0    355256   0% /var/lock
udev                    355256       500    354756   1% /dev
devshm                  355256         0    355256   0% /dev/shm
lrm                     355256     34696    320560  10% /lib/modules/2.6.22-14-generic/volatile
/dev/hda7             10080488    246860   9321560   3% /home
/dev/hda1             10241404   8506668   1734736  84% /media/hda1
/dev/hda5             30701232  29507552   1193680  97% /media/hda5
/dev/hda6             20472816  13328080   7144736  66% /media/hda6
/dev/hdb1             40313964  33469876   4796204  88% /media/hdd1
/dev/hdb2             80636072  53393972  23145928  70% /media/hdd2
/dev/hdb3              5542308    142208   5118564   3% /media/hdd3

and the contents of /media look like so
total 68
 0 lrwxrwxrwx  1 root root        6 2007-09-19 18:35 cdrom -> cdrom0
 4 drwxr-xr-x  2 root root     4096 2007-09-19 18:35 cdrom0
 4 drwxr-xr-x  2 root root     4096 2007-09-19 18:35 cdrom1
 0 lrwxrwxrwx  1 root root        7 2007-09-19 18:35 floppy -> floppy0
 4 drwxr-xr-x  2 root root     4096 2007-09-19 18:35 floppy0
 8 drwxrwx---  1 root plugdev  8192 2008-04-05 10:05 hda1
16 drwxrwx--- 20 root plugdev 16384 1969-12-31 19:00 hda5
16 drwxrwx--- 10 root plugdev 16384 1969-12-31 19:00 hda6
 4 drwxrwxrwx 16 root root     4096 2008-03-28 19:06 hdd1
 8 drwxrwxrwx 13 root root     8192 2008-04-05 18:48 hdd2
 4 drwxrwxr-x  3 root anand    4096 2007-09-22 21:03 hdd3

Any ideas what is wrong?
Tx

---

