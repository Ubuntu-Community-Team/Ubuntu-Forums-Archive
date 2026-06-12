---
title: "repositories"
date: 2007-02-08
forum: General Help
---

### Post by scottym on 2007-02-08
when updating repositoreies in synaptic i am getting the following errors:
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

Can anyone shed some light on this please?

---

### Post by disturbedite on 2007-02-08
i read in another post that a possible solution might be to get the gpg key.

or try:
apt-get clean  then
apt-get update

---

