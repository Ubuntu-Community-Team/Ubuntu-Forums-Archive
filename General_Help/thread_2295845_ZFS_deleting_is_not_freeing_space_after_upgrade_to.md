---
title: "ZFS deleting is not freeing space after upgrade to zfs-dkms:amd64 0.6.5-2~trusty"
date: 2015-09-21
forum: General Help
---

### Post by MasterMaxus on 2015-09-21
Hi People,

I recently ran an apt-get update && apt-get upgrade.

The install log: [http://pastebin.com/LZg7xrGG](http://pastebin.com/LZg7xrGG)

Once the install completed, I discovered all my ZFS mounts suddenly had 0 free space when they had at least 80GB prior to the update.

```

> sudo zpool status storage
NAME      SIZE  ALLOC   FREE  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
storage  10.9T  10.6T   332G         -    10%    97%  1.00x  ONLINE  -

```

I then deleted about 30GB of data:

After deleting nothing changed:

```

> sudo zpool status storage
NAME      SIZE  ALLOC   FREE  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
storage  10.9T  10.6T   332G         -    10%    97%  1.00x  ONLINE  -

```

I also did a ZFS pool upgrade as it was complaining mine was out of date, thinking this might resolve the issue but it seems to have had no effect on the drive space issue.

This all looks similar to this issue: [https://github.com/zfsonlinux/zfs/issues/1548](https://github.com/zfsonlinux/zfs/issues/1548) (but a unmount and remount did nothing)

```

> sudo zpool status storage
  pool: storage
 state: ONLINE
  scan: scrub repaired 0 in 20h49m with 0 errors on Tue Sep 22 01:49:58 2015
config:

        NAME        STATE     READ WRITE CKSUM
        storage     ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            sdb     ONLINE       0     0     0
            sdc     ONLINE       0     0     0
            sdd     ONLINE       0     0     0
            sde     ONLINE       0     0     0

errors: No known data errors

```

appears to be nothing wrong with the drives either.

Also I don't have any snapshots:

```

> sudo zfs list -t snapshot
no datasets available

```

This one has me a bit stumped, anyone have any ideas or suggestions?

Thanks!
A

---

### Post by MasterMaxus on 2015-09-22
I've deleted a stack of data off and now its showing that there is free space.

if the drive was full how was i able to delete stuff that was there and still not free up space? Its as if the space went into negative?

```

sudo zpool list
NAME      SIZE  ALLOC   FREE  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
storage  10.9T  10.5T   369G         -     9%    96%  1.00x  ONLINE  -

```

I can see there is 369G free, but it only reports 16GB:

```

df -lah
Filesystem        Size  Used Avail Use% Mounted on
storage            16G     0   16G   0% /storage

```

I don't expect to have access to all 369G but space does seem to have shrunk.

---

### Post by lukeiamyourfather on 2015-09-24
ZFS deletes are asynchronous so if the machine is very slow, the disks are under high load, or there are many files it might take a while for the delete to actually occur on disk. Not sure if that's what you're experiencing here but it's something to be aware of.

---

### Post by MasterMaxus on 2015-09-24
Hi Luke,

Yeah i left it for a few days, not change there was def something weird going on there. I have since destroyed the pool and have recreated it.

Thanks for your help
M

---

### Post by lukeiamyourfather on 2015-09-25
Can you tell more about what kind of data was being deleted? If using compression like LZ4 on the file system a file could be many GB to the user but in reality occupy very little disk space if the data could be compressed a lot. For example uncompressed TIFF images might be hundreds of MB to the user but occupy only 20-30 MB on disk when using ZFS.

---

