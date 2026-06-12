---
title: "Getting 'cannot bind mount' errors trying to run snap package filebot"
date: 2016-12-18
forum: General Help
---

### Post by tk83 on 2016-12-18
I'm on Ubuntu 16.04, fully up to date, and trying to use filebot from the snap package. The package installed fine but I'm unable to actually run filebot:
```
$ filebot
cannot bind mount /var/lib/snapd/hostfs/var/lib/lxd -> /var/lib/lxd with flags 0x8500e. errmsg: Permission denied
$ sudo filebot
cannot bind mount /var/lib/snapd/hostfs/var/lib/lxd -> /var/lib/lxd with flags 0x8500e. errmsg: Permission denied
$ snap list
Name     Version  Rev  Developer    Notes
core     16.04.1  641  canonical    -
filebot  4.7.5    5    pointplanck  -

```

I'll have to revert back to using the Deb package version from their website for now, but would be interested if anyone knows why the snap package isn't working?

---

### Post by tk83 on 2017-01-06
This seems to have been because I'd moved my /var/lib/lxd to another partition with more space and made /var/lib/lxd a symlink to it. I changed it around so /var/lib/lxd was a normal directory and I only moved and symlinked its containers, images and snapshots sub-dirs

---

