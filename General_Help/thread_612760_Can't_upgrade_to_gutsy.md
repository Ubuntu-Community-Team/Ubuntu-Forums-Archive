---
title: "Can't upgrade to gutsy"
date: 2007-11-14
forum: General Help
---

### Post by infin?ty on 2007-11-14
I am not able to upgrade my fiesty fawn to gutsy gibbon i get the following error 

"Authenticating the upgrade failed. There may be a problem with the network or with the server. "

Wen i try 
```
gksu "update-manager -c -d"
```

i foloowing error
[CODE]
warning: could not initiate dbus
extracting '/tmp/tmpaGSzbd/gutsy.tar.gz'
authenticate '/tmp/tmpaGSzbd/gutsy.tar.gz' against '/tmp/tmpaGSzbd/gutsy.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information: 

gpg: WARNING: unsafe permissions on homedir `/tmp/tmpaGSzbd'

gpg: verify signatures failed: eof

[CODE]

Also wnever i try to update the sources


W: GPG error: http://archive.ubuntu.com feisty Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com feisty-backports Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com feisty-security Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com feisty-proposed Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com feisty-updates Release: The following signatures were invalid: NODATA 2


Cant figure out how to get over this problem, so someone plz help me out

---

