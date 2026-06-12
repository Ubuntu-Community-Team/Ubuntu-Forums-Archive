---
title: "[SOLVED] Dapper Updates: MD5Sum mismatch"
date: 2007-12-05
forum: General Help
---

### Post by pwaldo on 2007-12-05
Hi all,

I'm having problems getting Dapper updates:

```
root@cerberus:~# apt-get clean
root@cerberus:~# apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get:2 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/universe Sources
Get:4 http://us.archive.ubuntu.com dapper-updates/main Packages [253kB]
Get:5 http://us.archive.ubuntu.com dapper-updates/universe Packages [95.3kB]
Get:6 http://us.archive.ubuntu.com dapper-updates/main Sources [70.5kB]
Get:7 http://us.archive.ubuntu.com dapper-updates/universe Sources [14.3kB]
Fetched 433kB in 0s (665kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.bz2  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-amd64/Packages.bz2  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.bz2  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.bz2  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Here is my sources.list file:

```
root@cerberus:~# cat /etc/apt/sources.list
#
#  /etc/apt/sources.list
#


#
# dapper
#
deb     http://us.archive.ubuntu.com/ubuntu/     dapper main universe
deb-src http://us.archive.ubuntu.com/ubuntu/     dapper main universe
deb     http://us.archive.ubuntu.com/ubuntu/     dapper-updates main universe
deb-src http://us.archive.ubuntu.com/ubuntu/     dapper-updates main universe
deb http://security.ubuntu.com/ubuntu dapper-security main universe
deb-src http://security.ubuntu.com/ubuntu dapper-security main universe

```

Any info would be appreciated!

Paul

---

### Post by pwaldo on 2007-12-06
Well it appears that this was an upstream problem.  I tried again today and all is well.  Go figure..

---

