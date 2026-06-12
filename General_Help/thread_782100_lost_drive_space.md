---
title: "lost drive space?"
date: 2008-05-04
forum: General Help
---

### Post by k0rv3n on 2008-05-04
Hi

I'm kind of new to *inx and currently I'm trying out ubuntu.
I have 3 HHD in the computer and when I run "df -h" I get this output:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              46G   39G  3.9G  91% /
varrun               1008M  928K 1007M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   84K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
/dev/sda3             184G  114G   61G  66% /media/sda3
/dev/sdb1             367G  346G  2.6G 100% /media/sdb1
/dev/sdc1             459G  420G   16G  97% /media/sdc1
```

Now if you sum the "Used" and "Avail" for each drive its not equal to the "Size" column at all. How come?

Thanks

---

### Post by chrisccoulson on 2008-05-04
EXT3 filesystems have 5% space reserved by default for privileged processes, so that essential services continue to run correctly even if you use all available space. This space is neither used or available to you. If I take your root filesystem for example, which is 46GB:
(46*0.05)+3.9+39=45.2, which is nearly equal to 46GB, so it adds up ok.

You can disable this 5% reserved by:
```
sudo tune2fs -m 0 /dev/sdxx
```
...where /dev/sdxx is the device node for the volume (you can get this from your 'df -h' output). '0' is 0% - you could set this to something between 0 and 5 for a compromise.

---

### Post by k0rv3n on 2008-05-06
Thanks for the reply!

Is this used on all the drives?
Now I have set 0% on all drives except the root parition.

---

