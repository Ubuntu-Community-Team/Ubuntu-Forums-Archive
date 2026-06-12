---
title: "Question about backintime and subsequent cloud backups"
date: 2020-02-09
forum: General Help
---

### Post by sfmcfar on 2020-02-09
Hi, I need help concerning backintime and subsequent backups to cloud storage.   When I run daily backups of a directory structure the initial backup clearly backs up the entire directory structure to my backup location.  The log files of subsequent backups clearly show that only changes were backed up to the new backup set. When I run a du on the two - the initial and the incremental - the sizes of the two backup directories are approximately the same.   My understanding is that the actual space being taken up on the disk is not doubled since rsync does magic things with the inodes.  But the reason for my concern is that I'm now running weekly backups of the backintime backups to a cloud storage service, and it appears that the cloud storage sees my daily backups as all being separate entities and thus the size of the backup heading to the cloud is waaaay too big to manage.

Any suggestions?

Thanks

Stan

---

### Post by TheFu on 2020-02-09
> **sfmcfar said:**
> Hi, I need help concerning backintime and subsequent backups to cloud storage.   When I run daily backups of a directory structure the initial backup clearly backs up the entire directory structure to my backup location.  The log files of subsequent backups clearly show that only changes were backed up to the new backup set. When I run a du on the two - the initial and the incremental - the sizes of the two backup directories are approximately the same.   My understanding is that the actual space being taken up on the disk is not doubled since rsync does magic things with the inodes.  But the reason for my concern is that I'm now running weekly backups of the backintime backups to a cloud storage service, and it appears that the cloud storage sees my daily backups as all being separate entities and thus the size of the backup heading to the cloud is waaaay too big to manage.

Any suggestions?

Back-in-time uses hardlinks to minimize backup storage needs for each backup "set".  Not all storage supports that, especially some cloudy storage.  You'll need to do research on hardlink support with your cloudy storage provider. 

If they don't support it, then you'll need to change to a backup solution that doesn't use hardlinks.  **duplicity** and **rdiff-backup** do not.

If they do support hardlinking, then you'll need to learn to use the correct tool to ensure the links are correct transferred.

Many backup solutions which use hardlinks fail to track permission changes correctly over the different backup sets.  That can be a minor inconvenience or a total backup failure. Just depends.

Wikipedia has an article about hardlinking that is worth your time to understand. Yes, it uses inodes.

---

