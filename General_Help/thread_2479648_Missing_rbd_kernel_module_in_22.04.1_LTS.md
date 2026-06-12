---
title: "Missing rbd kernel module in 22.04.1 LTS?"
date: 2022-10-01
forum: General Help
---

### Post by zestysoft on 2022-10-01
Greetings!

I recently did a `do-release-upgrade` from 20.04.5 LTS to 22.04.1 LTS on a Raspberry PI 4.

Unfortunately I discovered that `/lib/modules/*/kernel/driver/block/rbd.ko` no longer exists.

Did that kernel module get moved into a different debian package?  It used to exist in linux-modules-*-raspi

RAdos block device (RBD) is a necessary piece for a distributed file system (rook-ceph) that's popular with the kubernetes folks.

---

### Post by deadflowr on 2022-10-02
It's in the linux-modules-extra-<version-string-here>-raspi packages now.
The extra package is now a suggested package so it won't automatically get installed.

---

