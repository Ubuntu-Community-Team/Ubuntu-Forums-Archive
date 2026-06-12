---
title: "tar incremental (-g) not reliably working"
date: 2015-01-11
forum: General Help
---

### Post by mike4ubuntu on 2015-01-11
I've been using tar -g <savelisting> for years for doing incremental backups.  It generally always worked.  However, now just recently, within a week or two, it won't do incremental backups for any files which are served by samba.  All other files not served by samba are ok.  Also, it's the file server running samba that is having the problem, not the remote hosts that have the files mounted smbfs(cifs).  So when the file server does the "tar -g", it's not even going through samba to get the files; they are local on its disks.  Just the fact that samba is sharing the files to other client hosts, causes the tar -g to do a full backup.  Even stranger, I run the "tar -g" right after midnight, but if I run it again during the day, it does the incremental backup ok.  It's as if samba is doing something right after midnight that is causing all files it sees to be considered modified/updated and/or accessed.  Anybody have any ideas?

using Ubuntu 14.04 with tar (GNU tar) 1.27.1.

---

