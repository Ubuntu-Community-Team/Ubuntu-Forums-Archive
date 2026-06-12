---
title: "Use disk from zfs importable pool to an active pool"
date: 2017-12-16
forum: General Help
---

### Post by ozgurerdogan on 2017-12-16
I need to replace disk for a zfs root installed system.
Previously it was:
 
```
NAME        STATE     READ WRITE CKSUM
        rpool       ONLINE       0     0     0
       mirror-0  ONLINE       0     0     0
          sda2      ONLINE       0     0     0
           sdb      ONLINE       0     0     0
```


And I had to replace first disk. And now it is:
```
NAME        STATE     READ WRITE CKSUM
        rpool       ONLINE       0     0     0
          sda2      ONLINE       0     0     0
```


sdb hold data.
```
pool: rpool-12312656247996879599
     id: 12312656247996879599
  state: DEGRADED
 status: One or more devices contains corrupted data.
 action: The pool can be imported despite missing or damaged devices.  The
        fault tolerance of the pool may be compromised if imported.
   see: http://zfsonlinux.org/msg/ZFS-8000-4J
 config:


        rpool-12312656247996879599  DEGRADED
          mirror-0  DEGRADED
            sda2    FAULTED  corrupted data
            sdb     ONLINE
```




And I want to create mirror and sync data from sdb to current mirror. What are the steps? Do I need to import old pool ?

---

### Post by lisati on 2017-12-16
*Thread moved to **General Help**.*

---

