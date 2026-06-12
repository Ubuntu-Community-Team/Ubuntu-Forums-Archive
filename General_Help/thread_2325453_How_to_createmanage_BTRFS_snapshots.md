---
title: "How to create/manage BTRFS snapshots"
date: 2016-05-22
forum: General Help
---

### Post by checoimg on 2016-05-22
This is where I'm at after installing with LVM. If you need more info just ask.


```
$sudo btrfs subvolume list /
ID 257 gen 24442 top level 5 path @

Filesystem             Size  Used Avail Use% Mounted on
udev                   1.8G     0  1.8G   0% /dev
tmpfs                  363M   39M  325M  11% /run
/dev/sda5              220G   29G  192G  13% /
tmpfs                  1.8G  182M  1.6G  10% /dev/shm
tmpfs                  5.0M  4.0K  5.0M   1% /run/lock
tmpfs                  1.8G     0  1.8G   0% /sys/fs/cgroup
/dev/sdb5              466G  290G  176G  63% /home
cgmfs                  100K     0  100K   0% /run/cgmanager/fs
tmpfs                  363M   48K  363M   1% /run/user/****
/home/user/.Private  466G  290G  176G  63% /home/user
```


```
$systemctl status lvm2-lvmetad.service
&#9679; lvm2-lvmetad.service - LVM2 metadata daemon
   Loaded: loaded (/lib/systemd/system/lvm2-lvmetad.service; enabled; vendor preset: enabled)
   Active: active (running) since vie 2016-05-20 13:57:24 AST; 2 days ago
     Docs: man:lvmetad(8)
 Main PID: 342 (lvmetad)
    Tasks: 1 (limit: 512)
   CGroup: /system.slice/lvm2-lvmetad.service
           &#9492;&#9472;342 /sbin/lvmetad -f

Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.

$ systemctl status lvm2-lvmetad.socket
&#9679; lvm2-lvmetad.socket - LVM2 metadata daemon socket
   Loaded: loaded (/lib/systemd/system/lvm2-lvmetad.socket; enabled; vendor preset: enabled)
   Active: active (running) since vie 2016-05-20 13:57:24 AST; 2 days ago
     Docs: man:lvmetad(8)
   Listen: /run/lvm/lvmetad.socket (Stream)

Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.
```

---

