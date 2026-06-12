---
title: "Can't write to hard drive, only read"
date: 2017-09-12
forum: General Help
---

### Post by 44daniel on 2017-09-12
I have a hard drive with a NTFS partition in my machine that I can only read and not write to.

lshw tells me this about the hard drive:
```
/dev/sdc1: LABEL="Cloud Drive" UUID="7AE8C9E1E8C99BAF" TYPE="ntfs" PARTUUID="098b9e73-01"
mount.fstype: fuseblk
mount.options: ro,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096

```
 
I think my problem is the "mount.options: ro" part. How do I change the "ro" to "rw"?

The hard drive doesn't appear in /etc/fstab
I am running Ubuntu Studio 17.04 installed to a ext4 partition on a different hard drive.

---

### Post by oldfred on 2017-09-12
Are you using Windows 8 or  10?
They use fast start up which is always on hibernation and it applies to all NTFS partitions that Windows sees.
The Linux NTFS driver will not auto mount a hibernated drive or one that needs chkdsk to prevent damage. It may mount read only  (ro).

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by 44daniel on 2017-09-14
This fixes my problem.
Thank you, oldfred. I had no idea the problem was caused by a Windows 8 setting, I had assumed it was caused by Ubuntu #-o

---

