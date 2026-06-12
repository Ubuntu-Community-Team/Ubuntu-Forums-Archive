---
title: "recovering xfs partition"
date: 2013-06-01
forum: General Help
---

### Post by scubascooby on 2013-06-01
My samsung telly uses a samsung external usb hard drive to record programmes to an xfs partition. Last year a power cut caused drive corruption on the xfs partition but I was able to recover it by assigning a new uuid, re-running the log etc.

A few weeks ago the partition went wrong again. I can read the other partitions but not the xfs one.

xfs_repair hust hangs and does nothing, can't even ctrl-C to kill it.

gparted can see the space used on the xfs (/dev/sdb3)  but that can't repair it either.


I only know the basics of repairing partitions so some suggestions would be appreciated.

---

### Post by scubascooby on 2013-06-02
How can I find out why the partition is not accessable ?

When I try a repair in gparted it says that an operation is pending. Is something locking the partition ?

---

### Post by scubascooby on 2013-06-02
I have tried xfs_check and xfs_repair but I am not sure if they are doing anything:

>> ps -A  | grep xfs
 1609 ?        00:00:00 xfsalloc
 1610 ?        00:00:00 xfs_mru_cache
 1611 ?        00:00:00 xfslogd
17110 ?        00:00:00 xfs-data/sdb3
17111 ?        00:00:00 xfs-conv/sdb3
17112 ?        00:00:00 xfs-cil/sdb3
17127 pts/1    00:00:00 xfs_repair

---

### Post by scubascooby on 2013-06-05
Well after numerous reboots, running xfs_repair with or without -L, gparted repair (just a shell to xfs_repair ?), and xfs-check about 100 times each it was able to do something to the partition and it is now working as well as it did before (not perfect), at least I have my video recordings back.

If only it worked the first time.

---

