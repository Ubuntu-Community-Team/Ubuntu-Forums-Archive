---
title: "rsnapshot and file permissions"
date: 2008-07-10
forum: General Help
---

### Post by sameerds on 2008-07-10
I use rsnapshot to take backups of my home directory. But when I checked on it, I realised that it failed to delete old files from the backup image, although "--delete" is specified in the rsync arguments. The problem is that the ".gvfs" directory in a user's home is not accessible to root. This causes an I/O error, and rsync skips delete operations, as it is supposed to.

This is not really a bug, but I suppose this will cause a problem on any Ubuntu system that uses rsnapshot out of the box. There are two options for me to fix this:

1) add ".gvfs" in the exclude list
2) add --ignore-errors to the rsync arguments

I am currently using the first option, since the second seems like an overkill to me. But now there's another concern: how do I know if yet another item causes such a problem? The only option I can see for now is to periodically examine the backup images. Instead, is there a way for rsnapshot or cron to notify me whenever rsync reports an error? This is a desktop system with just two users, and no email setup. So cron can't just generate an email for the root containing the output of a job.

---

