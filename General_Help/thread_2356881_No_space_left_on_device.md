---
title: "No space left on device"
date: 2017-03-27
forum: General Help
---

### Post by ceejayf on 2017-03-27
Hi,

I'm working with a relatively fresh installation of ubuntu server 16.04.1 LTS on a Gigabyte H97N-WIFI mainboard, a samsung SSD and two 6TB drives that I recently configured to run in a RAID1 configuration using mdadm.

Since finishing the RAID1 configuration, my system is running very slowly and any operation results in a "no space left on device' error, despite there being plenty of space and inodes.

```
cameron@gateway-pc:~$ mkdir test
mkdir: cannot create directory ‘test’: No space left on device
```

```
cameron@gateway-pc:/$ df -h
Filesystem                        Size  Used Avail Use% Mounted on
udev                              7.8G     0  7.8G   0% /dev
tmpfs                             1.6G  9.4M  1.6G   1% /run
/dev/mapper/gateway--pc--vg-root  102G  102G     0 100% /
tmpfs                             7.8G     0  7.8G   0% /dev/shm
tmpfs                             5.0M     0  5.0M   0% /run/lock
tmpfs                             7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1                         472M   57M  391M  13% /boot
tmpfs                             1.6G     0  1.6G   0% /run/user/1000
```

```
cameron@gateway-pc:/$ df -i
Filesystem                        Inodes IUsed   IFree IUse% Mounted on
udev                             2033023   607 2032416    1% /dev
tmpfs                            2038041   881 2037160    1% /run
/dev/mapper/gateway--pc--vg-root 6742016 93049 6648967    2% /
tmpfs                            2038041     1 2038040    1% /dev/shm
tmpfs                            2038041     4 2038037    1% /run/lock
tmpfs                            2038041    16 2038025    1% /sys/fs/cgroup
/dev/sda1                         124928   298  124630    1% /boot
tmpfs                            2038041     4 2038037    1% /run/user/1000
```
[COLOR=#28FE14][FONT=&amp]
[/FONT][/COLOR]I've since edited /etc/fstab to remove the RAID1 device, but the problem remains.

All of the support articles that I've uncovered seem to point to the problem being old kernels building up or inodes, but this doesn't seem to be the problem in my case.

Any ideas?

Thanks

---

### Post by TheFu on 2017-03-27
Please fix the post above using "code tags", not quotes. This will make it readable. Thanks.  Just too hard to read for me.

---

### Post by ceejayf on 2017-03-27
Done.

---

### Post by TheFu on 2017-03-27
Thanks.  The / partition, which includes /home/ is full.

```
/dev/mapper/gateway--pc--vg-root  102G  102G     0 100% /
```

You can use **sudo lvs** and **blkid** to see how the VGs, LVs and partitions are setup.
I would strongly recommend AGAINST adding the spinning disks to the gateway--pc--vg-root VG.  When things go badly, it will make solving the issue much harder.

It doesn't appear that the spinning disks (mdadm RAID) are mounted. If you want to use them, create a file system, create a mount point, them mount the array using the fstab settings.

All Unix systems run slowly when the / and /var partitions get full. Best to leave 1-5G free space on those partitions or LVs.

---

### Post by ceejayf on 2017-03-28
Awesome, thanks. I don't know how I missed that, but you're right of course. I'm cleaning up my downloads folder.

---

### Post by mörgæs on 2017-03-28
Good, if this solved your problem please mark the thread so.

---

### Post by TheFu on 2017-03-28
I'm not always right, but once in a while, even a blind squirrel finds a nut. ;)

The RAID disks weren't being used. If you still want that - there are many how-tos.  Disks don't automatically get a file system, nor are they mounted where you want them, automatically.  As the system Admin, it is your job to handle these things since there are probably 50 different file systems and millions of possible mount locations.  The defaults are seldom what I want.  Plus, using LVM is all manual for the setup, but usually worth it long-term for non-trivial needs.

---

