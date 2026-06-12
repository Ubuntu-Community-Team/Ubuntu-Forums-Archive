---
title: "&quot;Bind&quot; entries in fstab aren't bound at boot if they refer to NFS mounts"
date: 2008-02-19
forum: General Help
---

### Post by Emblem Parade on 2008-02-19
My fstab includes NFS mounts, which are correctly mounted at boot. Things like this:

```
192.168.1.100:/family /mnt/family nfs rw,auto 0 0
```

That's all good. However, my fstab also includes bind mounts that reference these NFS mounts. For example:

```
/home/family /mnt/family none bind,rw,auto 0 0
```

Unfortunately, these don't get mounted at boot. I have to manually enter "sudo mount -a" after boot. I imagine this has to do with how NFS works -- it needs networking to run, so it probably processes fstab after the bind mechanism does.

Does anyone have an idea on how to elegantly automate these bind mounts?

---

