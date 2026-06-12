---
title: "mirror a folder to a mounted share - NFS/SMB/CIFS"
date: 2007-09-12
forum: General Help
---

### Post by neill on 2007-09-12
hi

i want to simply mirror /home to a remote mounted share /mnt/backup/home

the share is permanently mounted in fstab and can be NFS or SMB/CIFS

/home contains a number of users data so the process needs to run with su privileges and it must also be able to be run unattended as a cron job

files in the mirrored directory should be recoverable with standard file tools

no need for SSH or anything clever

no need for increments, snapshots, differential backups - just a plain mirror

any suggestions/recommendations ??

thanks

/neill

---

### Post by AndyCooll on 2007-09-12
I'm pretty sure you could use rsync with a line in the cron for the purpose.

:cool:

---

### Post by neill on 2007-09-12
i'll give it a whirl - thanks

---

