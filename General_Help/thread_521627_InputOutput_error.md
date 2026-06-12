---
title: "Input/Output error"
date: 2007-08-09
forum: General Help
---

### Post by darrenc on 2007-08-09
After just going through losing my networking because of something windows did to my nic, I have a residual problem I can't get resolved.  I have an external linkstation harddrive that I mount to /mnt/link by fstab at boot.  Obviously, when my nic was dead it couldn't mount the drive.  But now that my nic is working again, the /mnt/link directory has somehow become corrupted.

If I try to mount it, it reports "could not resolve mount point /mnt/link".  If I try to delete it (or rename it), I get a reply saying "cannot lstat 'link': Input/Output error".

For the time being, I've created a new mount point (link1) and it mounts fine, but I really need the other one back.  Many, many things point to that mount point.  Plus, just opening the /mnt directory now takes about 2 minutes because of that corrupt folder in it.

I've tried booting into recovery mode, just on the off chance that might let me have access to it, but I just get the same error message when I try to delete it.

---

### Post by apetresc on 2007-08-09
That sounds like a corrupted inode. I assume /mnt is ext3? In that case you should run a fsck and see if it gets picked up.

---

### Post by darrenc on 2007-08-09
Thanks.  Took a bit of fighting with it, but it eventually worked.  Oddly, when it deleted the corrupt mount point, another mount point in the /mnt folder corrupted.  Ran fsck again and deleted that one, then a third corrupted.  Then I just deleted them all and recreated them, and so far it's all working.

That's making me think I might be needing a new hard drive soon.

But again, thanks.

---

