---
title: "reduce pyhsical vhdx size - Hyper-V 2012"
date: 2014-08-27
forum: General Help
---

### Post by ranc1d2 on 2014-08-27
Hello everyone,

i'm running Ubuntu 12.04.4 LTS (GNU/Linux 3.5.0-36-generic x86_64) as a virtual machine on a Windows Server 2012.
I use this virtual server to host [seafile]("http://www.seafile.com/en/home/").

I have two dynamic virtual hard disks, one for system (on ssd) and one for the seafile data.
As you can see in the attached image the vhdx disk files on my datastores grew to 32GB and 133GB.

This is the current disk usage on the server:
```
Filesystem              Size  Used Avail Use% Mounted on
/dev/mapper/sonic-root   49G  2.6G   44G   6% /
proc                       0     0     0    - /proc
sysfs                      0     0     0    - /sys
none                       0     0     0    - /sys/fs/fuse/connections
none                       0     0     0    - /sys/kernel/debug
none                       0     0     0    - /sys/kernel/security
udev                    233M  4.0K  233M   1% /dev
devpts                     0     0     0    - /dev/pts
tmpfs                    49M  268K   49M   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    243M     0  243M   0% /run/shm
/dev/sda1               228M   53M  163M  25% /boot
/dev/mapper/data-data   148G   81G   60G  58% /mnt/data
/mnt/data/seafile-data  148G   81G   60G  58% /opt/seafile/seafile-data

```

As you can see there is a lot of unused space inside the vhdx after the used 2.6GB/81GB (the free space comes from the subsequent move of seafile-data to a second disk and from the deletion of seafile content).
Is there any way to get this unused space truly unused? 
The following step would be a shrink/convert/clone of the vhdx-file on Hyper-V to shrink it to the really used space.

As disk space on ssd is always precious any help to reclaim some would be appreciated.

thx in advance
Stefan

---

