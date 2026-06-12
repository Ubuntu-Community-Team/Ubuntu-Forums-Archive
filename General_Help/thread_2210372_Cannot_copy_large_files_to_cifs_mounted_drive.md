---
title: "Cannot copy large files to cifs mounted drive"
date: 2014-03-10
forum: General Help
---

### Post by p-bickford on 2014-03-10
I am running Ubuntu 13.10 and cannot backup (or copy large files) to a network server (an asdl router with harddrive from free.fr). It copies data for about 30 seconds, then it slows down to a crawl. The syslog gives the following errors:

```
CIFS VFS: sends on sock --------------- stuck for 15 seconds
CIFS VFS: Error -11 sending data on socket to server
```

For example, when I copy a large file (using Samba/CIFS), the first 353 MB transfer within seconds - two hours later, it has transferred less than 1 MB more, then completely gives up.

For backups, I have tried the Ubuntu backup application, plus LuckyBackup and BackInTime (all of which use rsync). The result is the same - the application will copy files for about 30 seconds, then hang.

The fstab entry is:

```
//xxx.xxx.xxx.xxx/share /media/backup_share cifs ounix,guest,uid=1000,gid=samb,rw,dir_mode=0775,file_mode=0775,iocharset=utf8 0 0
```

---

