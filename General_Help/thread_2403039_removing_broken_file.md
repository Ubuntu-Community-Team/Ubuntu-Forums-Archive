---
title: "removing broken file"
date: 2018-10-06
forum: General Help
---

### Post by sniper8752 on 2018-10-06
I have a broken file that looks like this:
```
d?????????  ? ?    ?       ?            ? shared_space
```
When I do a rm -rf on it, it says "rm: cannot remove 'shared_space': Is a directory".
How do I remove this file?

---

### Post by TheFu on 2018-10-06
This can be causes by a corrupt file system or a missing mount (storage for the mount is missing).  umount the file system and run fsck if it is a local disk.  If it is network storage, umount the disk on the server where it is physically attached and run fsck, then restart what ever sharing service is providing the network storage.

---

