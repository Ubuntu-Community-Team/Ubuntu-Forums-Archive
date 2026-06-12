---
title: "Backup Failed"
date: 2019-06-08
forum: General Help
---

### Post by frankdn01 on 2019-06-08
Ubuntu 18.04.2...

Deja-dup fails during verification, complaining that there is not enough "Temp space" available.  Is this a configurable parameter?

---

### Post by TheFu on 2019-06-08
I don't use deja-dup or duplicity for backups. Google found this:

[https://askubuntu.com/questions/191653/deja-dup-backup-change-use-of-tmp-to-another-folder-location](https://askubuntu.com/questions/191653/deja-dup-backup-change-use-of-tmp-to-another-folder-location)
```
export TMPDIR=/othervolume/otherfolder  ; deja-dup-preferences
```

Don't change /tmp/ to be somewhere else.

---

### Post by cruzer001 on 2019-06-08
I think simplicity in backup has been lost, hence/since grsync.  I backup home and call it good :)

---

### Post by frankdn01 on 2019-06-08
Thanks!  That seems to have done the trick.

---

