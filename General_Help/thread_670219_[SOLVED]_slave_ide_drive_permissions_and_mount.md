---
title: "[SOLVED] slave ide drive permissions and mount"
date: 2008-01-17
forum: General Help
---

### Post by timboellis on 2008-01-17
Right been having major issues with my internal IDE drive a 500gb drive

I have tried various things to get it to work always getting permission issues.

However I have now managed to backup the whole drive so trying to start from fresh

I installed QTParted formatted it to ext3 made it active mounted it on fstab by

/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  2  
and also tried
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  2  

However the disc is now only showing 80gb and still not writable.

So can anyone help with this as I say it is fresh so i can delete partitions format it etc. 

My fstab as it stands
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda6
UUID=d59d14a2-0dc0-4eed-93fa-0522caf97786  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=17dacc52-0317-47ca-b33b-5a0735ca8413  none           swap         sw                          0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec            0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec            0  0  
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  2  [/PHP]
[PHP]tim@Timbo:~$ ls -l /media
total 14
drwxr-xr-x 2 root root 4096 2008-01-17 02:18 backup
lrwxrwxrwx 1 root root    6 2008-01-14 19:34 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-01-14 19:34 cdrom0
dr-xr-xr-x 8 root root 2048 2008-01-12 21:42 cdrom1
drwxr-xr-x 2 root root 4096 2008-01-14 23:25 sdb1
[/PHP]
[PHP]tim@Timbo:~$ ls -l /media
total 14
drwxr-xr-x 2 root root 4096 2008-01-17 02:18 backup
lrwxrwxrwx 1 root root    6 2008-01-14 19:34 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-01-14 19:34 cdrom0
dr-xr-xr-x 8 root root 2048 2008-01-12 21:42 cdrom1
drwxr-xr-x 2 root root 4096 2008-01-14 23:25 sdb1
[/PHP]

---

### Post by timboellis on 2008-01-17
FINALLY !!!!!!!!!!!!!!!!!!!!

Well I was close I think.

What I had done was tried many times to mount as Back.Backup,SDB etc.

So I done sudo nautalis , then deleted the old folders then changed the permissions within the file manager over to my user and gave full access and to others full access and can write happyly now

---

