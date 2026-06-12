---
title: "Systemd (sd-executor) failed with exit status 1, failed to fully start up daemon"
date: 2022-08-19
forum: General Help
---

### Post by Krischu on 2022-08-19
A hosted UBUNTU 18.04 LTS server (32bit) fails to boot up. On the system console I can only see:

```
Welcome to Ubuntu 18.04.6 LTS!

systemd[1]: Set hostname to <mail.domain.org>
systemd[383]: Failed to open serialization file: Read-only file system
systemd (sd-executor) failed with exit status 1
systemd[1]: Failed to fully start up daemon
[!!!!!!] Failed to startup up manager
systemd[1]: freezing execution
```

Last thing that happened was that the system disk ran out of capacity. I mounted the disk in a rescue system, freed space, fsck'd the disk (was clean)
but rebooting gives again the picture above.

Any clues?

---

### Post by Krischu on 2022-08-19
Solved it (had the same problem some time ago) Solution:
```

apt remove snapd
```

Now how can I disable snapd forever from being updated or installed?

---

