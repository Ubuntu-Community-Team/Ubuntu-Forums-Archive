---
title: "wwwoffle"
date: 2005-09-20
forum: General Help
---

### Post by ubuntuubuntu on 2005-09-20
When I try to install wwwoffle by "apt-get install wwwoffle", I get the following error message:
Reading package lists... Done
Building dependency tree... Done
wwwoffle is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up wwwoffle (2.8d-1) ...
Checking for htdig package...
Fixing up user's preference of spool-dir
(adding symlink to it as /var/cache/wwwoffle)... done.
mkdir: cannot create directory `/var/cache/wwwoffle': File exists
mkdir: cannot create directory `/var/cache/wwwoffle': File exists
mkdir: cannot create directory `/var/cache/wwwoffle': File exists
  creating /var/cache/wwwoffle/monitor symlink
ln: creating symbolic link `/var/cache/wwwoffle/monitor' to `../../lib/wwwoffle/monitor': No such file or directory
dpkg: error processing wwwoffle (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 wwwoffle
E: Sub-process /usr/bin/dpkg returned an error code (1)

 What should I do?
Thank you!

---

### Post by Xian on 2005-09-20
Try removing the complaining path and try again:

```
$ sudo rmdir /var/cache/wwwoffle
```

---

### Post by ubuntuubuntu on 2005-09-21
I've done that and, for some reason, I still get the same message. What should I do?
Thank you!

---

### Post by Xian on 2005-09-21
Try purging the application then re-installing it.

```
$ apt-get remove --purge wwwoffle
$ apt-get install wwwoffle
```

---

