---
title: "local console spam about overlayfs: missing 'lowerdir'"
date: 2020-06-22
forum: General Help
---

### Post by kjstech on 2020-06-22
I'm running Ubuntu 20.04 LTS in a Hyper-V VM soley to run grafana and collect network statistics for my home network.

The local console is getting spammed with alternating messages:
aufs aufs_fill_super:918mount[6090]: no arg
overlayfs: missing 'lowerdir'


Everything seems to be working fine and there's no message spam on the SSH session... its only on the local console.

Anything I can do to stop these messages?

---

### Post by kjstech on 2020-07-01
I got the console spam to stop by running sudo apt-get remove snapd

No idea what that is, I dont use any of this, found it from googling and seeing this on my system

df -t squashfs
Filesystem     1K-blocks   Used Available Use% Mounted on
/dev/loop2         99456  99456         0 100% /snap/core/9289
/dev/loop4        128896 128896         0 100% /snap/docker/461
/dev/loop5        128896 128896         0 100% /snap/docker/471
/dev/loop7         31104  31104         0 100% /snap/snapd/7777
/dev/loop9         30592  30592         0 100% /snap/snapd/8140
/dev/loop1         56320  56320         0 100% /snap/core18/1705
/dev/loop3         56320  56320         0 100% /snap/core18/1754
/dev/loop8         98944  98944         0 100% /snap/core/9436
/dev/loop10        73088  73088         0 100% /snap/lxd/15855
/dev/loop6         72960  72960         0 100% /snap/lxd/15878

---

