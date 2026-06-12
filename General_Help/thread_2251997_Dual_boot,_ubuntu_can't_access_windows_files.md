---
title: "Dual boot, ubuntu can't access windows files"
date: 2014-11-08
forum: General Help
---

### Post by dsm2 on 2014-11-08
Hi.
I had ubuntu 14.04 and windows 10 technical preview. Recently I deleted windows partition using GParted because I didn't need windows anymore.
Now when I try to open my partition drives, it says:

```
Unable to access “Data”
Error mounting /dev/sda5 at /media/dsm/Data: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda5" "/media/dsm/Data"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```

Before I deleted windows, I had turned "fast boot" off from both windows and my bios setups.
What Should I do?

---

### Post by Mark Phelps on 2014-11-08
Running CHKDSK in Windows typcally fixes this, but since you removed Windows, that is not easy for you to do.

Consider downloading and burning a CD from the ISO file of the Minitool Partition Wizard Boot CD.  That's a Windows partitioning tool and, after you boot from it, you can run a Check operation on the Windowns filesystem partition, and that should fix the problem.

---

### Post by dsm2 on 2014-11-14
> **Mark Phelps said:**
> Running CHKDSK in Windows typcally fixes this, but since you removed Windows, that is not easy for you to do.

Consider downloading and burning a CD from the ISO file of the Minitool Partition Wizard Boot CD.  That's a Windows partitioning tool and, after you boot from it, you can run a Check operation on the Windowns filesystem partition, and that should fix the problem.

Thanks so much :) It worked.

---

