---
title: "fstab - fmask and dmask"
date: 2004-12-10
forum: General Help
---

### Post by BigSandwich on 2004-12-10
Well I know what umask does, but I keep seeing fmask and dmask.  I cant seem to find a man page or anything.  I just wondered what they do and I'm kinda beginning to obsses about it.

---

### Post by AndersAA on 2004-12-10
man umask, they are basicaly that specific for files/directories :)

---

### Post by p!=f on 2004-12-10
> **BigSandwich]Well I know what umask does, but I keep seeing fmask and dmask.  I cant seem to find a man page or anything.  I just wondered what they do and I'm kinda beginning to obsses about it.[/QUOTE]

```

:~ $ man mount

```
 said:**
> 
umask=value
Set  the  umask  (the bitmask of the permissions that are not present). The default is the umask of the current process.  The value is given in octal.

dmask=value
Set the umask applied to directories only.  The default is the umask of the current process.  The value is given in octal. Present since 2.5.43.

fmask=value
Set  the  umask applied to regular files only.  The default is the umask of the current process. The value is given in octal. Present since 2.5.43.


---

