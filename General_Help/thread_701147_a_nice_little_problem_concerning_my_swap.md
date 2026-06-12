---
title: "a nice little problem concerning my swap"
date: 2008-02-19
forum: General Help
---

### Post by jocheem67 on 2008-02-19
[HTML]jochem@ubuntu:~$ sudo -s
[sudo] password for jochem:
root@ubuntu:~# free
             total       used       free     shared    buffers     cached
Mem:       2076268     393504    1682764          0      14908     215128
-/+ buffers/cache:     163468    1912800
Swap:            0          0          0
root@ubuntu:~# gedit /etc/fstab
root@ubuntu:~# swapoff -a
root@ubuntu:~# swapon -a
root@ubuntu:~# free
             total       used       free     shared    buffers     cached
Mem:       2076268     492420    1583848          0      22948     274476
-/+ buffers/cache:     194996    1881272
Swap:      2570392          0    2570392
root@ubuntu:~# [/HTML]

Here we go:
As you can see I have a managable swapfile, can put it off and on, seems okay....

However when I boot I'm getting an fstab error:

"warning: bad line in /etc/fstab line 8"

Fstab:

[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=dcdda7a5-5611-4e2c-808b-4946964a4de1 /               ext3    defaults,errors=remount-ro 0       1
/dev/sdc2        none            swap    sw              0       0
    
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sda5       /media/Backup   ntfs    defaults,force,umask=007,gid=46 0       1
/dev/sdb1       /media/Windows  ntfs    defaults,force,umask=007,gid=46 0       1
/dev/sdb5       /media/Progs    ntfs    defaults,force,umask=007,gid=46 0       1[/HTML]

I've been fooling around with the livecd creating, shrinking partitions and have really tried to intimidate my gutsy-install....
Rsult is that I lost the UUID for my /dev/sdc2, which I think resulted in this bad line message...

Has anyone any idea how to get rid of this message, getting back the UUID?
Maybe someone notices some faulty line in my fstab?

---

### Post by vanadium on 2008-02-19
line 8 is an empty line in the output you posted. To reuse the UUID, you can replace the device name (/dev/sdc2) by UUID="XXXX..XX" which you can directly copy into your fstab from within the output of the command "blkid". Apart from that your line for the swap partition is not using UUID, it looks fine and I don't think tat is causing the error.

---

### Post by jocheem67 on 2008-02-19
[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=dcdda7a5-5611-4e2c-808b-4946964a4de1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc2        
UUID=b59164f2-f464-40a9-8794-6c1027366a9a none            swap    sw              0       0 
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sda5       /media/Backup   ntfs    defaults,force,umask=007,gid=46 0       1
/dev/sdb1       /media/Windows  ntfs    defaults,force,umask=007,gid=46 0       1
/dev/sdb5       /media/Progs    ntfs    defaults,force,umask=007,gid=46 0       1[/HTML]

Here's my output once more, problem solved, so thanks a lot!!!!!

( Guess it was idd the empty line causing the error....)

---

