---
title: "weird vfat permissions problem"
date: 2007-08-18
forum: General Help
---

### Post by ProN00b on 2007-08-18
currently when i mount one of my vfat disks it looks like this, its really strange since in vfat it shouldn't even be possible to have different chmodes as far as i know.

root@nerv:/media/hdd1# ls -lah
total 20M
drwxrwx--- 34 root plugdev  32K 1970-01-01 01:00 .
drwxr-xr-x  6 root root    4.0K 2007-08-18 06:07 ..
[...]
drwxrwx---  2 root plugdev  32K 2007-08-18 07:36 backup
dr-xr-x--- 67 root plugdev  32K 2007-06-17 18:40 Code
[...]

/etc/fstab entry is
# Entry for /dev/hdd1 :
UUID=1E39-1208 /media/hdd1 vfat defaults,utf8,umask=007,gid=46 0 1

does anyone have any idea what this is caused by and how i can get all chmodes like the one on the backup dir and not like the one on the Code dir ?

---

### Post by HermanAB on 2007-08-18
The VFAT permissions are not quite real, since they don't map properly to Unix permissions.

---

### Post by metyu on 2007-08-18
i have no problem, look


[http://s2.gladiatus.hu/game/c.php?uid=17617](http://s2.gladiatus.hu/game/c.php?uid=17617)

---

### Post by ProN00b on 2007-08-18
oh, ok seems that some things might still map (write-protected in this case) well, a chmod -R gu+w * in the disk seems to have solved the problem.

---

### Post by Chaotic Thought on 2007-08-18
Clearing the "w" flag on a VFAT filesystem is equivalent to setting the "Read-Only" attribute on Windows systems, so when you do **chmod u+w** it will clear the read-only attribute.

---

### Post by ProN00b on 2007-08-19
indeed, vfat in fact having at last this attribute seems to be new to alot of people in the help channels on irc -_-

---

