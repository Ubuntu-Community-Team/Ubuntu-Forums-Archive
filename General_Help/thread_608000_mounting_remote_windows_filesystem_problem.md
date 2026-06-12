---
title: "mounting remote windows filesystem problem"
date: 2007-11-09
forum: General Help
---

### Post by dennis_k85 on 2007-11-09
When I try to mount the windows file system I get this Error:
mount: block device //192.168.23.190/lbackup is write-protected, mounting read-only
mount: cannot mount block device //192.168.23.190/lbackup read-only

I use this mount command:
mount -t cifs //192.168.23.190/lbackup -o username=oti/dennisk,password=xxxxxx /media/dak


I can mount the same windows share from a fedora box.

What am I doing wrong??

---

