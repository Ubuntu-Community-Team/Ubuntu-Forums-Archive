---
title: "[SOLVED] hard drives mounted as read only"
date: 2007-08-07
forum: General Help
---

### Post by notatoad on 2007-08-07
my hard drives all seem to mount as read only, i cannot change the owner with (sudo) chown, and i cannot add myself as the user with (sudo) chmod

fstab looks like this
```
/dev/hda1    /mnt/320    rw,user,auto   0   0
```

and the same options for two more drives.  what's going on?

---

### Post by notatoad on 2007-08-07
nevermind, a reboot fixed it.  wierd.

---

