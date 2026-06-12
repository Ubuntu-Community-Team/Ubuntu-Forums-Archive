---
title: "How-to remove zram from lubuntu"
date: 2013-12-05
forum: General Help
---

### Post by marinara on 2013-12-05
Before removing zram, read [this]("http://wiki.gentoo.org/wiki/Zram").  There doesn't seem to be much downside to leaving zram on.  For some situations, zram will reduce the amount of memory available for caching, i think this is rare.  So unless you have a server that needs lots of caching for disk access, while at the same time you have a large memory hogging applications that you don't care if they swap.  That is the prime case for turning off zram

how to remove zram:
1. as root type:
```
apt-get remove --purge zram-config

```

should be ok to remove lubuntu-desktop as I believe it's only a metapackage

another way to remove zram is:
[http://ubuntuforums.org/showthread.php?t=2189961&p=12857312#post12857312](http://ubuntuforums.org/showthread.php?t=2189961&p=12857312#post12857312)

consider turning on zswap.  it's also in lubuntu 13.10 you just need to edit your grub config and reboot

---

