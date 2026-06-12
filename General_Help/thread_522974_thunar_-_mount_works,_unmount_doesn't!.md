---
title: "thunar - mount works, unmount doesn't!"
date: 2007-08-11
forum: General Help
---

### Post by lapsey on 2007-08-11
I have much confusion with unmount rights with thunar on a new memory device. i already have chmod u+s `which mount` `which umount` etc

An older device, IPOD, mounts and unmounts fine as user. but the new device, KODAK_PC, cannot unmount well via thunar. 

> "Cannot unmount the volume 'KODAK_PC', Details: Cannot remove directory"

Permissions for devices and mount points are identical across the board, and IPOD has not had to be listed in fstab or anything else like that.

However:

> drwx------  4 me root    4096 1970-01-01 01:00 IPOD
drwxr-xr-x  2 me me  4096 2007-05-07 12:14 iso
drwx------  3 me root   **16384** 1970-01-01 01:00 KODAK_PC


what's up?

---

