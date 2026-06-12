---
title: "Mount CIFS share on LTS 12.04 - files stored locally"
date: 2014-01-21
forum: General Help
---

### Post by Simon_Green on 2014-01-21
Hi all,

Appreciate if anyone could advise on the following.

I'm mounting a CIFS Windows share [\\'servername'\backups]("file://\\'servername'\backups") onto /backups on a Ubuntu Server 12.04 LTS. When this is mounted files deposited in the mount point are appearing in the Windows share but also appear to be being stored locally in the /backups folder on the server. If I umount the share then the backups folder still appears on the Ubuntu server and it contains all of the files?

What I want to achieve is that the files stored in the mount point are not stored locally on the server.

Appreciate if anybody could advise what I'm doing wrong.

Many thanks,

Simon

---

### Post by TheFu on 2014-01-21
Perhaps you accidentally ran the backups when the remote mount wasn't active, thus putting a bunch of files under /backups.
When you mount the remote file system, it overlays (hiding) the local files. You can test this by creating a file before the remote CIFS mount in /backups ... **touch /backups/test-file-0012**, then do the mount and look for that file. It won't be there.  umount /backups/ and the file will return.

Make sense?

BTW, this is a common thing.  My backup jobs validate that the backup file system is mounted before starting. This avoids filling the root file system by accident.

---

