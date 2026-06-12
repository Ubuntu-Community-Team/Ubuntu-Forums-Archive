---
title: "How to remove a copy of an encrypted folder created with Déjà Dup"
date: 2016-01-23
forum: General Help
---

### Post by fangorn2 on 2016-01-23
I use Déjà Dup to make backups of my Private folder, encrypted with ecryptfs.
Usually I use ecryptfs-mount-private straight after I log in, because Déjà Dup starts its backups at system startup and there is no way to use schedulers.
Today I forgot to run ecryptfs-mount-private on time, so Déjà Dup made a backup of my encrypted Private folder.
I restored the last backup to check the result and I found an enrypted copy of my Private folder.
I tried to delete it unsuccessfully and received this warning: "There was an error deleting Access-Your-Private-Data.desktop. Error removing file: Permission denied".
What can I do?
I am also concerned about my backups. If Déjà Dup allowed it, I would delete the last backup because I am afraid my last backup messed up my incremental backups.

---

