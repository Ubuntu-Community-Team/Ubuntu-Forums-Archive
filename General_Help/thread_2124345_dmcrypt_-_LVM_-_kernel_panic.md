---
title: "dmcrypt - LVM - kernel panic"
date: 2013-03-10
forum: General Help
---

### Post by stfu on 2013-03-10
Hi,

I have Ubuntu 10.04 running on a XenServer 5.6. After a failed drive on RAID5 I can no longer boot up Ubuntu. After asking for password to decrypt the device /dev/sda5 it says: Kernel panic - not syncing: Attempted to kill init!

I booted up rescue system with Ubuntu install CD and was able to get to busybox prompt. After entering password on dmcrypt device, I can get the filesystem to show mounted as /target. However when i try to chroot /target I can't use any commands such as ls.

```

#ls: error while while loading shared libraries: libattr.so.1: cannot open shared object file: No such file or directory

```

There's error on most of the commands I try. Also /target/bin/bash is missing. /target/boot is empty

Most of the files seem to be in /target/ - but for example /target/etc/ is missing.

Is there a way to fix this?

---

