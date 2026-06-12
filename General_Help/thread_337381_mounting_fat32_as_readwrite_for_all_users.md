---
title: "mounting fat32 as read/write for all users"
date: 2007-01-12
forum: General Help
---

### Post by wunderbar on 2007-01-12
Hi, I'm trying to mount a fat32 drive as read/write for all users, without having to sudo.

I've mounted it in the command line, I've tried adding to fstab.  I've tried chmod 777 that entire directory, but it wont' give read/write to all users, just root.  the command goes through with no errors(tried verbose so I saw what happened), however, it does not alter the permissions  I've also even tried chown to make my account the owner of the directory, but it does also will not change anything.

help?

---

### Post by dcstar on 2007-01-13
> **wunderbar said:**
> Hi, I'm trying to mount a fat32 drive as read/write for all users, without having to sudo.

I've mounted it in the command line, I've tried adding to fstab.  I've tried chmod 777 that entire directory, but it wont' give read/write to all users, just root.  the command goes through with no errors(tried verbose so I saw what happened), however, it does not alter the permissions  I've also even tried chown to make my account the owner of the directory, but it does also will not change anything.

help?

Have you tries the **umask** setting in your /etc/fstab file?

Here is the line in my file:
```
UUID=0020-4649                             /media/hda1     vfat         defaults,utf8,umask=007,gid=1000,noatime  0  1
```

---

