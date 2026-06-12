---
title: "Proftpd + MySQL jailing user home directories"
date: 2012-10-24
forum: General Help
---

### Post by ezjacob on 2012-10-24
Hey ya'll don't know if this is possible or not. But I have a bunch of virtual users in a MySQL db and have ProFTPD setup to use the info to login ftp users. So a sample table entry is

```
userid | passwd  | uid  | gid  | homdir               | shell
ejacob | test123 | 4004 | 4400 | /home/someRandomUUID | /sbin/nologin
```

the homedir column is /home/someRandomUUID

now when the ftp user logs in it creates the user home dir in /home/someRandomUUID and jails the user to that directory using DefaultRoot.

Is it possible to have ProFTPD append another location for all ftp user home dirs that it receives **WITHOUT** changing the table entry.

So instead of **/home/someRandomUUID** I would like it to be located **/var/ftpdata/home/someRandomUUID**. I rather not mess with the table if all at possible. This helps separate my ftp user homedir and system user homedirs. Thanks for any input in this.

---

