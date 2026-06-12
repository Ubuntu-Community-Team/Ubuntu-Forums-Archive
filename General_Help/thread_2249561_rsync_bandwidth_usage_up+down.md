---
title: "rsync bandwidth usage up+down"
date: 2014-10-23
forum: General Help
---

### Post by trekkiejonny on 2014-10-23
I wanted to make a local repository mirror of Trusty i386+amd64 so I decided to use debmirror. Followed the guide [https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror) and it worked great. However I noticed that during the time it did its mirroring it transmited just as many gigabytes as it recived. My traffic monitor for that day shows 123.99 GB Reception & 115.51 GB Transmission. So my question is why the massive upload?

here is the command I use, editited for easier viewing
```
debmirror
--checksums
--method=rysnc
--no-source
--host=mirrors.us.kernel.org
--root=/ubuntu
--arch=i386,amd64
--section=main,restricted,universe,multiverse,main/debian-installer,universe/debian-installer,multiverse/debian-installer,restricted/debian-installer
--dist=trusty,trusty-updates
/repository
```

---

### Post by tgalati4 on 2014-10-23
Presumably, if your mirror is exposed to the Web, then perhaps you were serving debian package files to the masses?   The apache log files should have a list of files served.

---

### Post by trekkiejonny on 2014-10-23
Apache has not yet been installed, haven't gotten around to that step. However apt-cacher-ng was installed but not visible outside my local network as the router had no forwards to it.

Interestingly enough apt-cacher-ng is no longer installed nor is its cache directory. Will look at the logs when I get home, brake over.

---

### Post by trekkiejonny on 2014-10-23
Nothing in apt or dpkg logs about the removal of apt-cacher-ng, must have been deleted by debmirror on its cleanup. Does debmirror have a log file? Can't find one it /var/log.

---

### Post by trekkiejonny on 2014-10-30
Bump, still would like to figure out why Debmirror used twice the bandwidth. Is it just normal for the intial mirroring?

---

