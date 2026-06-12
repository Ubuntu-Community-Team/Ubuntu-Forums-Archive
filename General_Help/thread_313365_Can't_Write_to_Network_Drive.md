---
title: "Can't Write to Network Drive"
date: 2006-12-05
forum: General Help
---

### Post by theh3brewhammer on 2006-12-05
I finally got my network drive setup and working, here's the line in fstab:
```

//hammer/Big    /media/Hammer smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

```
I can read the drive fine, but cannot write to it.  Windows is setup to allow all users read/write access.  I thought dmask and fmask are currently setup to give read/write permission?  Thanks for the help.

---

