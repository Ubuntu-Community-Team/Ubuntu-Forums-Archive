---
title: "LUKS partition becomes read-only"
date: 2007-01-24
forum: General Help
---

### Post by etienne.navarro on 2007-01-24
Sometimes on a mounted LUKS partition, it suddenly becomes read-only and nothing can be written to it.
When issuing the command:
```
sudo mount -o remount /dev/mapper/luks
```it says the device is write protected. A complete unmount normally fixes the problem.
I have had this happen on two different computers with two different hard drives. So its not a problem with the hardware.

Has anyone experienced this?

---

