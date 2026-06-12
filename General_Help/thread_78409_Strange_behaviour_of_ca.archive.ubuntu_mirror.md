---
title: "Strange behaviour of ca.archive.ubuntu mirror"
date: 2005-10-18
forum: General Help
---

### Post by Rounan on 2005-10-18
May be nothing, but the ca mirror is doing strange things. After an apt-get update using ca.archive.ubuntu.com:

```
Reading package lists... Done
W: GPG error: http://ca.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

$ sudo apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  gksu
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 50.2kB of archives.
After unpacking 0B of additional disk space will be used.
```

Trying to install gives a 404 error on the gksu.deb.

But when I switch to archive.ubuntu.com (no ca) and apt-get update, there's no signature error and the gksu package isn't shown as an update. The wrong GPG sig and the nature of the package (rootkit?) have me worried.

---

### Post by Kyral on 2005-10-18
It seems like most of the regional mirrors (ca, us, etc) are having problems. Use plain "archive.ubuntu.com"

Its no root kit (Install chkrootkit and run it if you feel like it ;D)

---

