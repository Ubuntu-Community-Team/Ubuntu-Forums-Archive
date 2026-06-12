---
title: "BTRFS Incremental Backup"
date: 2016-03-15
forum: General Help
---

### Post by ian77 on 2016-03-15
Hi All,

I am in the process of migrating my physical home NAS server to a virtual machine (also ran at home). I have transferred my data into a btrfs file system (as used on my physical server)  on the new server and it's working as I expect.

Previously I rsynced data to separate hard drive and ran an incremental update daily. This worked fine.

However, for my new set up I want to take advantage of btrfs snapshots and incremental backups between snapshots as this is faster and has other benefits over rsync.
I am having trouble with running the backup manually, as described in the wiki [https://btrfs.wiki.kernel.org/index.php/Incremental_Backup](https://btrfs.wiki.kernel.org/index.php/Incremental_Backup)

**Current BTRFS setup**

2 btrfs file systems:

sudo btrfs fi show /data

> Label: none  uuid: 4b940013-16fb-4b17-a472-5d39d7029353
        Total devices 1 FS bytes used 3.05TiB
        devid    1 size 3.63TiB used 3.06TiB path /dev/mapper/data-data

sudo btrfs fi show /backup
> 
Label: none  uuid: 854ad203-d3ed-4397-9c8f-b082facea44c
        Total devices 1 FS bytes used 416.00KiB
        devid    1 size 3.63TiB used 2.04GiB path /dev/sdc1

**Software**
btrfs version: btrfs-progs v4.4.1
kernel: 3.19.0-51-generic
ubuntu 14.04



**Problem and Error**

I encounter an error when initially trying to send a read only snapshot

sudo btrfs send /data/snapshots/13-3-16-2303/ | btrfs receive /backup/snapshots/

> ERROR: can't perform the search - Operation not permitted
ERROR: cannot resolve our subvolid: -1
At subvol /data/snapshots/13-3-16-2303/

When I try without sudo:
> 
ERROR: check if we support uuid tree fails - Operation not permitted
ERROR: failed to initialize subvol search: Operation not permitted
ERROR: can't perform the search - Operation not permitted
ERROR: cannot resolve our subvolid: -1

So I'm stuck at the first hurdle and can't figure out what to do.
Nothing gets written to the system logs when this error occurs. I've looked through manuals and google and I can't figure it out.

Hoping someone can help.

Cheers,

Ian

---

### Post by ian77 on 2016-03-17
Missed the second sudo needed in the transfer command after the pipe.

Instead of:

> sudo btrfs send /data/snapshots/13-3-16-2303/ | btrfs receive /backup/snapshots/

It should be:

> sudo btrfs send /data/snapshots/13-3-16-2303/ | **sudo** btrfs receive /backup/snapshots/

Silly omission. Seems to be backing up fine now.

---

### Post by papibe on 2016-03-17
Hi ian77.

You can also do this:
```
 sudo bash -c 'btrfs send /data/snapshots/13-3-16-2303/ | btrfs receive /backup/snapshots/' 
```
Regards.

---

