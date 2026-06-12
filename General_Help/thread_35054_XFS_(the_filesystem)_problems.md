---
title: "XFS (the filesystem) problems"
date: 2005-05-17
forum: General Help
---

### Post by ifrs on 2005-05-17
Hello friends!

Several months ago (with warty) I've had the same problem with the XFS filesystem on two different computers: during heavy filesystem load (e.g. copying files >1GB and/or filling the filesystem up to 98%) the filesystem suddenly "disappeared" and reading/writing files was no more possible. "xfs_repair" was helpful and the problem seems to be gone after updating to the new kernels from warty-security.

But today (with hoary) I've lost many hours of computation time because the filesystem became corrupted during the job. The partition (200GB) is on an external harddisk (250GB) connected through firewire (I've resolved some firewire specific problems with the "serialize_io" option).
The last time I've checked the job about 70GB of data was already written to the the disk (together with other data about 100GB filled the partition).

Here's the log:

scsi0 (0:0): rejecting I/O to device being removed
Buffer I/O error on device sda3, logical block 25378917
lost page write due to I/O error on sda3
... (last message repeated for several blocks)
scsi0 (0:0): rejecting I/O to device being removed
... (last message repeated many times)
I/O error in filesystem ("sda3") meta-data dev sda3 block 0xba47867       ("xlog_iodone") error 5 buf count 1536
xfs_force_shutdown(sda3,0x2) called from line 952 of file fs/xfs/xfs_log.c.  Return address = 0xd0314e6c
Filesystem "sda3": Log I/O Error Detected.  Shutting down filesystem: sda3
Please umount the filesystem, and rectify the problem(s)
xfs_force_shutdown(sda3,0x1) called from line 353 of file fs/xfs/xfs_rw.c.  Return address = 0xd0314e6c
... (last message repeated several times)

Mounting the filesystem after restarting the harddisk didn't work (after reconnecting the harddisk became sdb):

XFS: Filesystem sdb3 has duplicate UUID - can't mount

Even running xfs_repair didn't help (with -L option to the remove the journal).

So the questions are:
- Is there any way to restore the data resp. fixing the UUID problem?
- Any recommendations for mount options for XFS filesystems (I used: noatime, async) which prevent such errors?
- Any recommendations for another filesystem on an external firewire disk?
- Can this be an Ubuntu specific problem because I've switched from Debian and had never such issues with XFS (the external firewire disk is new, but the problems I mentioned with warty appeared on the same computer configurations).


Thanks,

Robert

---

### Post by ifrs on 2005-05-17
Ok, at least not all data is lost. Restarting and reconnecting the harddisk was not enough. After a reboot I was able to mount the partition without an error.

---

