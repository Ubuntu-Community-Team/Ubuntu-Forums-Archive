---
title: "Volume mounting error"
date: 2015-09-23
forum: General Help
---

### Post by MMOneT3Q on 2015-09-23
I installed Ubuntu 15.04 today. For some reason, I'm unable to access my hard drives. These are 4TB HDDs, formatted NTFS and they work perfectly fine with Windows.

This is the error on one of them:

```
Error mounting /dev/sdc2 at /media/media/Downloads: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdc2" "/media/media/Downloads"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdc2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


```

Same error for all 4 HDDs.

I have shut down Windows fully & properly before installing Ubuntu though (and removed Windows then). Any idea how this can be fixed? I need them in read-write mode.

Cheers

---

### Post by MMOneT3Q on 2015-09-23
Hey. You can mark it as solved.

In case someone got here with the same problem, the following command solves it:

```
sudo ntfsfix /dev/sdc2
```

Obviously replace [SIZE=2][FONT=courier new]sdc2 [/FONT][/SIZE]with whatever that's relevant.

---

