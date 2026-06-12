---
title: "Mounting cifs share not working for normal user after s bit is set"
date: 2008-03-05
forum: General Help
---

### Post by Meson on 2008-03-05
```
//<winpc>/<share> /mnt/<mntpoint> noauto,users,credentials=<certfile>,uid=<normaluser>,file_mode=0400,dir_mode=0500
```

I'm using this line in my fstab to mount a windows share from a normal user.  I have added the s-bit to /sbin/mount.cifs.  I've even tried adding it to mount as well.  I still get this error:
```
mount error: permission denied or not superuser and mount.cifs not installed SUID
```

If it helps, I tried adding the s bit to truecrypt some time ago to mount encrypted volumes as a normal user but it didn't work either.

---

