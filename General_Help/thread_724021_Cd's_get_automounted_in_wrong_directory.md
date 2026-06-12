---
title: "Cd's get automounted in wrong directory"
date: 2008-03-14
forum: General Help
---

### Post by symon1980 on 2008-03-14
Hi Peoples
Im having a problem with the automounting of my cd drive.
whenever i put a cd in, it mounts it to media:/hdb instead of /media/cdrom.
How do i fix this? here is the info in my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=53cdd001-47a2-47c7-a1b1-9d7fe7052638 / ext3 defaults,erro$
# /dev/sda5
UUID=7c292ef6-33eb-49e3-8b8a-8343d1d9963f none swap sw $
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

its a real problem for me, cause when i try to install games for example, with multiple cd's, i can install the first by browsing, but then i can't install the rest cause its pointing it in the wrong directory. and theres nothing there
thanx :)

---

### Post by kpkeerthi on 2008-03-14
While I don't have a fix for your issue, I suggest a workaround you may try
1. Insert the CD
2. When you see it mounting to a wrong directory, unmount it with
```
sudo umount /dev/hdb
```
3. Do not remove the CD from the drive yet. Just remount it to /media/cdrom0 (or whereever the program is expecting it to be present)
```

sudo mount /dev/hdb /media/cdrom0
```

---

