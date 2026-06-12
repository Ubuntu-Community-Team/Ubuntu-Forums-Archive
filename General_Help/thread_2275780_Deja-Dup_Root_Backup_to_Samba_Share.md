---
title: "Deja-Dup Root Backup to Samba Share"
date: 2015-04-28
forum: General Help
---

### Post by vni.jamie on 2015-04-28
I'm trying to perform a backup to a samba share as the root user.

There is no problem backing up to the share when running Deja-Dup with my normal user credentials.

When I run ```
gksu deja-dup-preferences
```, and enter the same backup location. Deja-Dup creates the backup under ```
~/smb:/WORKGROUP;jamie@192.168.X.Y/backup
```

I've tried entering the path to the share as a custom location but this didn't help.

Do I need to mount the samba share as root before doing the backup?

---

