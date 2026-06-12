---
title: "external drive won't load"
date: 2013-09-28
forum: General Help
---

### Post by ELD on 2013-09-28
So for no apparent reason my external hard drive fails to mount:

```

Error mounting /dev/sdb1 at /media/liam/Liams Storage: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/liam/Liams Storage"' exited with non-zero exit status 12: Failed to read last sector (976773103): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

I haven't changed any configuration on it at all, it just popped up.

---

### Post by TheFu on 2013-09-28
I'd run chkdsk and/or scandisk on it from Windows.  Perhaps it wasn't closed down properly the last time?
The HDD could be failing - time to make a bit-for-bit backup using ddrescue, clonezilla, fsarchive, whatever other tool you use.
The cable or disk controller or USB port or USB controller could be failing.  That is assuming this is a USB drive. If eSATA, the same ideas apply.
The bits could be lazy and just need refreshing.  A full backup and restore should do that too.

Sorry, nothing obviously jumps out.

---

