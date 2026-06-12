---
title: "Rollback from ZFS snapshot"
date: 2018-06-28
forum: General Help
---

### Post by danik56 on 2018-06-28
I am running 18.04 on a full disk native ZFS root file system.
Right after initial install I have created a full disk image backup using Clonezilla.
I have made several ZFS snapshots of the root file system over time and exported them to a remote storage server.

Now, suppose at some point I will need to replace the system disk and would then restore the Clonezilla backup image.
Would it be possible at that point to receive the snapshots back from the remote site and restore the root file system from the latest snapshot ?

---

### Post by TheFu on 2018-06-28
[https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS) has example scenarios for most ZFS needs.  But it also says 
> Also note that ZFS is only supported for data storage, not the root filesystem. 
Limitations like that usually happen for good reasons.

Some more from the examples:
> For example, make a snapshot and save it to a file:

```
sudo zfs snapshot -r mypool/projects@snap2
sudo zfs send mypool/projects@snap2 > ~/projects-snap.zfs
```

..and receive it back:

```
sudo zfs receive -F mypool/projects-copy < ~/projects-snap.zfs
```
The file example is good, because files are a generic type of object in Unix and can be representative for any stream.

I need to get some ZFS on my media server.  Just been putting it off.

---

### Post by danik56 on 2018-06-28
> **TheFu said:**
> [https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS) has example scenarios for most ZFS needs.  But it also says 

Limitations like that usually happen for good reasons.

Some more from the examples:

The file example is good, because files are a generic type of object in Unix and can be representative for any stream.

I need to get some ZFS on my media server.  Just been putting it off.


Suppose I boot from LiveCD, and access the real ZFS root file system when it is not being used as the running system root.
Would that allow me to restore the root file system from a snapshot ?
Does a ZFS snapshot contain all actual data of the file system at the time the snapshot was taken ?

Is there another way to backup the root file system from the running system so it can be restored in an event of disaster ?

---

### Post by TheFu on 2018-06-28
Try it. Does it work?

---

### Post by danik56 on 2018-06-29
> **TheFu said:**
> Try it. Does it work?

I think we are on to something.

After restoring the Clonezilla image and re-booting from LiveCD, I was able to access the ZFS file system on the system drive by issuing:

zpool import zpool1    (zpool1 is the pool name where the root file system lives) 

At this point I was able to RECEIVE the most recent snapshot of the root file system from a network device as if it was just a regular file system. (I used the -F option on the receive command) 
Then I did a ROLLBCAK using the received snapshot.

After re-booting to the real system, all files and installed packages seem to be up to date reflecting the point in time when the snapshot was taken.

---

### Post by TheFu on 2018-06-29
If this is solved, please mark the thread as solved to help others out.
ZFS is pretty cool, huh?

---

### Post by danik56 on 2018-06-29
Yep. Very cool.

---

