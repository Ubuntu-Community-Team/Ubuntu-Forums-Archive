---
title: "NFS mount of a nested FileSystem not showing data from nested mount"
date: 2020-07-11
forum: General Help
---

### Post by egandt on 2020-07-11
On my Source I have the following:

/raid6 (a 55TB raid6 drive) with a directory /raid6, however I have a high performance NVMe mounted as /raid6/public/fast (for scratch space), this works great locally.

On a destination I mount this device /raid6/public using NFS as /fileserver/public again no problem I can see data in /raid6/public/WORKSTATION as /fileserver/WORKSTATION as it should be, but when I access /fileserver/fast I get the directory structure that /radi6/public/fast  mounts over, but not the data on /radi6/public/fast.  (They have the same structure in case the mount of the NVMe fails the system can still operate).

I tried also setting an NFS mount directly to: /raid6/public/fast so that /raid6/public/fast-> /fileserver_fast
Again only data on raid6 and not on the drive mounted under /raid6/public/fast is present in the NFS mount, which is driving me crazy what should it matter what is mounted where as long as the parent path is mounted everything under that should also be visible, why it NFS not showing data on a sub mounted drive, but only the parent, while an mount SMB shows it correctly in say Windows.

I figure part of the issue is that by exporting /raid6/public/ the export to /raid6/public/fast is not even used, but the root of the issue is that NFS is not reading data from a drive mounted under another drive.

So the test case: is mount /A share it via NFS you get all data in /A now mount a second disk as /A/B   the data in /A/B is inaccessible when mounted via NFS, but is locally, yet I can not see any reason why this is the case or a way to resolve it.  Might mention SMB has no such issue, this seems to be only NFS.

Thanks,
ERIC

---

### Post by dinkidonk on 2020-07-12
Look at the **crossmnt** and **nohide** options in the [exports manpage]("https://linux.die.net/man/5/exports").

---

