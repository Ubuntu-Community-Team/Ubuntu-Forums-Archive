---
title: "Disk Config Confusion"
date: 2007-10-04
forum: General Help
---

### Post by cmnorton on 2007-10-04
I remember back in July when I built my first Ubuntu 6.06 system, I had (or thought I had) /home on a second, larger IDE drive. Now after two upgrades, I cannot figure out what I have.  So, my questions are as follows. What happened to the two-disk configuration; is it configured properly; and if it is not configured properly, how do I fix it?

This system has two IDE drives, a 40 GB and a 200GB.

Here's df's output. To the best of my knowledge, I do not have a SCSI or SATA drive in this system.

cnorton@linux-testU:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             37001804  23956340  11165864  69% /
varrun                  254008       240    253768   1% /var/run
varlock                 254008         4    254004   1% /var/lock
procbususb              254008       112    253896   1% /proc/bus/usb
udev                    254008       112    253896   1% /dev
devshm                  254008         0    254008   0% /dev/shm
lrm                     254008     34504    219504  14% /lib/modules/2.6.20-16-386/volatile
cnorton@linux-testU:~$ 

Here's what the link for home looks like:

cnorton@linux-testU:~$ ls -ld /home
lrwxrwxrwx 1 root root 14 2007-06-19 12:32 /home -> /mnt/hdb1/home
cnorton@linux-testU:~$ 

Here's what's out on /mnt/hdb1

cnorton@linux-testU:/mnt/hdb1$ ls -l
total 12
drwxr-xr-x 6 root root 4096 2007-07-09 12:56 home
drwxrwxrwx 3 root root 4096 2007-06-19 15:20 samba_shares
drwxr-xr-x 3 root root 4096 2007-07-09 14:09 tmp
cnorton@linux-testU:/mnt/hdb1$ 

And, here's fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=ec94d7ad-6480-443f-bbe7-44c6fa1e2e96 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=5b16941c-1903-426b-9375-afc5e60ccadc none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
~

---

### Post by themoebius on 2007-10-05
from looking at your fstab it would appear that /dev/hdb1 isn't being mounted at all, at least not automatically. Now, I'm assuming you want the ENTIRE 200GB drive to be your home directory? If that is the case, I think you can mount it directly at the /home mount point. You should add an entry to your fstab mapping /dev/hdb1 to /home. But then you will also have to move around your files on hdb because you have a separate home directory already inside of it. If you mount it to the /home mountpoint everything you currently see in /mnt/hdb1 will appear inside of /home.

---

### Post by cmnorton on 2007-10-05
I believe one of the problems I am having is that the Edgy install modified the notion of hda1 and hdb1. They're replaced with sda1. 


Edit:
Thanks for your input. /dev/sdb is the second IDE drive.

---

