---
title: "error in mounting"
date: 2013-08-03
forum: General Help
---

### Post by Rifa_Wadood on 2013-08-03
I cant access my disk volume and get following msg and pls help me to solve:

Error mounting /dev/sda2 at /media/rifa/New Volume: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/rifa/New Volume"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by The Cog on 2013-08-03
It would probably be best to use a windows OS to run chkdisk on the volume, which should remove the "unclean" indication from it.

If you can't do that, you could run 
```
sudo ntfsfix -d /dev/sda2
```
which might do the trick. But if there are already problems on the filesystem (that windows chkdisk could have fixed but ntfsfix can't) it might make things worse.

The ntfs filesystem is undocumented and secret to Microsoft. So the open-source tools have limited ability to repair problems with ntfs volumes.

---

