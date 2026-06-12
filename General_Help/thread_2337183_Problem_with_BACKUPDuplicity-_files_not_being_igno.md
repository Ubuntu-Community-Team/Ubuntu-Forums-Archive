---
title: "Problem with BACKUP/Duplicity- files not being ignored as directed"
date: 2016-09-15
forum: General Help
---

### Post by Dan Z on 2016-09-15
running 14.04

Use BACKUPS with Duplicity

I have several Directories excluded, yet, when Backup runs I get errors that they cannot be backed up.

Backup tells to to check and see if open

home/dan/.gconf/apps/gnome-schedule/templates
/home/dan/.gvfs

both are excluded from backup, so why does it even try?

Dan

---

### Post by TheFu on 2016-09-16
Can't help without seeing the exact, total, complete, command entered. Please use code tags.  Also, the EXACT error would be helpful too.

---

### Post by Dan Z on 2016-09-18
Hello-

No commands available, was through GUI.

Screenshots attached

Dan

---

### Post by TheFu on 2016-09-18
Can't help. Sorry.

---

### Post by Dan Z on 2016-09-23
problem solved kind of

All these were ROOT,

Changed group to NOT ROOT.

All problems gone.

Dan

---

