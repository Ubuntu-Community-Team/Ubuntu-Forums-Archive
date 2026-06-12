---
title: "Free Disk space gradually disappears. Contradictory reports from df / du."
date: 2014-04-09
forum: General Help
---

### Post by ZippZapp on 2014-04-09
OS: Ubuntu Hardy Server 8.04
DISK: RAID1 using 2 identical 320GB disks, both partitioned as 315GB + 5GB
md0 = sda1 + sdb1  
md1 = sda2 + sdb2
(sdc1 is a 1TB usb-disk for backup)

I have got a terrible problem with disk space virtually disappearing. **Almost 200GB is not accounted for!**
The real usage of the 315GB partition is less than 120GB, but still I need to move more and more data to other places in order to keep it from reporting as full.
I need some input in order to identify what is making more and more of the disk "invisible" for usage.
(I have already scanned for Trash-folders and deleted the few files found, but one a few MB worth of files, but it is obviously did not help much)

df reports a full md0:

```
$ df -Th
```
outputs:
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/md0      ext3    289G  282G     0 100% /
varrun       tmpfs   1007M  444K 1007M   1% /var/run
varlock      tmpfs   1007M     0 1007M   0% /var/lock
udev         tmpfs   1007M   80K 1007M   1% /dev
devshm       tmpfs   1007M   12K 1007M   1% /dev/shm
overflow     tmpfs    1.0M   44K  980K   5% /tmp
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon    289G  282G     0 100% /home/users/bjorn/.gvfs
/dev/sdc1  fuseblk    932G  932G     0 100% /media/My Passport___

```

....but using 'du' shows something else, only 119 GB can be seen as used here:

```
$ sudo du -h --max-depth=1 /
```
outputs:
```
26M     /root
4.8M    /bin
du: cannot access `/home/users/bjorn/.gvfs': Permission denied
113G    /home
324M    /boot
1.1T    /media
4.0K    /mnt
64K     /lost+found
44K     /tmp
252K    /dev
0       /sys
1.7G    /lib
4.0K    /initrd
4.0K    /srv
3.1G    /usr
6.9M    /sbin
du: cannot access `/proc/8123/task/8123/fd/4': No such file or directory
du: cannot access `/proc/8123/task/8123/fdinfo/4': No such file or directory
du: cannot access `/proc/8123/fd/4': No such file or directory
du: cannot access `/proc/8123/fdinfo/4': No such file or directory
0       /proc
4.0K    /opt
702M    /var
22M     /etc
3.7M    /lib32
1.2T    /   **(~119 GB (disregarding '/media' containing also ~1GB usb-disk)**

```



Any hints, suggestions and ideas are highly appreciated, - I feel stuck at the moment. #-o

Best regards,
ZippZapp

---

### Post by Dreamer Fithp Apprentice on 2014-04-10
You might try k4dirstat if you haven't already.

---

### Post by sotiris2 on 2014-04-10
290 GB are on /home/users/bjorn/.gvfs
Not sure what you can do about that though.

---

### Post by Dreamer Fithp Apprentice on 2014-04-10
Might this be relevant?:
[https://bugs.launchpad.net/ubuntu/+source/simplebackup/+bug/227753](https://bugs.launchpad.net/ubuntu/+source/simplebackup/+bug/227753)

---

