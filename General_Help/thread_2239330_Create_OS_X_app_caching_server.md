---
title: "Create OS X app caching server"
date: 2014-08-13
forum: General Help
---

### Post by Andy_Carver on 2014-08-13
The apple OS X server app has a caching system that can cache downloads from apple. 

Here. [https://www.apple.com/au/support/osxserver/cachingservice/](https://www.apple.com/au/support/osxserver/cachingservice/)

It's pretty friggen awesome. Is there a way to make this on Ubuntu?

---

### Post by TheFu on 2014-08-13
Uh .... apt-cacher-ng? I don't know anything about OSX, don't know how that compares.

You can also setup your own PPA for distributing software locally, but that is more for developers, not system admins.  Or just mirror the repos with rsync but that's wasteful on storage and bandwidth.

My apt-cacher-ng stats:
```

Allocated disk space (Top 10)
1.9 GiB	security.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages.bz2
976 MiB	security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages.bz2
799 MiB	uburep/dists/trusty/main/binary-amd64/Packages.bz2
525 MiB	security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-amd64/Packages.bz2
276 MiB	security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages.bz2
258 MiB	uburep/dists/precise-updates/main/binary-amd64/Packages.bz2
256 MiB	uburep/dists/trusty/universe/binary-amd64/Packages.bz2
225 MiB	uburep/dists/trusty/main/binary-i386/Packages.bz2
152 MiB	uburep/dists/trusty/universe/binary-i386/Packages.bz2
141 MiB	uburep/dists/precise/main/binary-amd64/Packages.bz2

```
And during patch cycles, over 90% of the packages are reused, but obviously some systems are not that similar, so some packages are only installed on 1 or 2 systems and the cache doesn't help too much.

---

### Post by tgalati4 on 2014-08-13
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

---

