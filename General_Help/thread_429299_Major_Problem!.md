---
title: "Major Problem!"
date: 2007-05-01
forum: General Help
---

### Post by merlinus on 2007-05-01
I have really screwed up this time, trying to move /home to a new partition.

I tried following the directions at pussycats, but in the midst of the process, having moved /home to /home_backup, I inadvertently closed the terminal window, and then nothing worked.

So I booted from the Live CD, where I am now.

I have a backup of my old /home as /home_backup, but cannot do anything with it.

I have mounted the various partitions using the file manager, but terminal commands such as

 sudo mount -t ext3 /dev/sda8/recovery

do not work.

The mounts I can see on the desktop are disk, which is the filesystem and contains a directory /home which is empty, and a directory home_backup, which contains a subdirectory merlin, and disk-1, where is where I attempted to move /home.  disk-1 contains a directory merlin, which used to be a subdirectory of /home.

/etc/fstab also seems totally trashed.

Help is greatly appreciated!

Thanks.

-merlin

---

### Post by merlinus on 2007-05-01
If this can aid in someone helping, System/Administration/System Monitor/File Systems lists the following:

device                  directory

/dev/sda8             /media/disk

/dev/sda7            /media/disk-1

---

