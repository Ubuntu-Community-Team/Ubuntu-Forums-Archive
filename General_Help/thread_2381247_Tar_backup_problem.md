---
title: "Tar backup problem"
date: 2017-12-28
forum: General Help
---

### Post by Bigfoot73 on 2017-12-28
I am trying to make a backup using tar like this:
*sudo tar -cvpzf backup.tar.gz --one-file-system /some_dir*
(as described here: [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR))
Assume /some_dir has this content:
*drwxrwx--x 2 someuser  somegroup 4096 jan 28  2017 some_sub_dir*
Then I will get this error message:
*tar: /some_dir/some_sub_dir: Cannot open: Permission denied*

Why? It's clear that root has no direct read access, but shouldn't I be able to add a complete directory to an archive when using *sudo tar* regardless of owners and access rights in subdirectories?

---

### Post by sisco311 on 2017-12-28
You have to exclude the virtual filesystems such as [GVfs]("https://en.wikipedia.org/wiki/GVfs") from the backup. 


What's the exact error message?

---

### Post by Bigfoot73 on 2017-12-28
> **sisco311 said:**
> You have to exclude the virtual filesystems such as [GVfs]("https://en.wikipedia.org/wiki/GVfs") from the backup. 

Thanks. I recently moved the files to another host (and mounted in the old location), so that explains why I get this result and why I haven't seen it before.

---

