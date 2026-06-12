---
title: "Write access to windows host partition"
date: 2008-05-11
forum: General Help
---

### Post by pentarious on 2008-05-11
Hi,
I've just installed Ubuntu 8.04 with Wubi and I can access the host partition from: /host/. Unfortunately, write access is granted only to the root user:
> cd /host/myPersonalStuff
> ls -l
-rwxr-xr-x 1 root root 10 2008-05-12 02:41 test
Since the host partition is internally handled I have no way to modify mount options, so I'm stuck. I have another NTFS partition (non-host partition) which is instead accessible with write access:
> cd /media/myDisk
> ls -l
-rwxrwxrwx 1 root root      12288 2008-05-12 01:35 test
Is that really the way Wubi is supposed to work? No write access to any folder/file in the host partition?
Any clue?

---

### Post by ago on 2008-05-14
That depends on the permissions you have on the windows side. You might try to change the permissions from within Ubuntu (sudo chmod) or the ownership (sudo chown).

---

