---
title: "Mount problems after disabling RAID"
date: 2012-11-14
forum: General Help
---

### Post by Confusedus on 2012-11-14
I have two internal hard disks.  When I originally installed kubuntu these were set up as a RAID which I've disabled
```
dmraid -rE /dev/sdb
```Initially after rebooting I had some problems that the /home partition couldn't be found.  I have edited fstab and can now boot fine HOWEVER, sdb2 is being mounted as the / partition even though in fstab I specify sda2.

Output of tail /etc/fstab

```

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /       ext3    errors=remount-ro,user_xattr    0       1
/dev/sda3       /home   ext3    defaults        0       0
/dev/sda1       none    swap    sw      0       0

```Output of df
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb2              9612516   7987220   1137004  88% /
none                   1523460       292   1523168   1% /dev
none                   1527824         0   1527824   0% /dev/shm
none                   1527824        88   1527736   1% /var/run
none                   1527824         0   1527824   0% /var/lock
none                   1527824         0   1527824   0% /lib/init/rw
/dev/sda3            226847108 203556008  11767876  95% /home

```

The problem might be that sda2 and sb2 share the same UUID.  Thanks in advance.

---

