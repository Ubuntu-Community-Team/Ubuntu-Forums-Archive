---
title: "failed to open package info file /var/lib/dpkg/status using recovery"
date: 2014-04-21
forum: General Help
---

### Post by daveayw on 2014-04-21
I recently repartitioned my hard drive to install 14.04 alongside my 12.04 LTS, long story short I had a few bad blocks that caused the resize to fail, which I repaired using fsck. Now 12.04 is unbootable, which I don't mind, I just would like to get a package list so I can install that on 14.04. When I drop into a root prompt for recovery I get the error when running 'dpkg -l': dpkg-query: error: failed to open package info file /var/lib/dpkg/status. Any help would be greatly appreciated or if there is another method I can use to obtain a package list that would help immensely. I've already migrated my home folder so if I can get the package list I can just trash the 12.04 partition entirely.

---

### Post by daveayw on 2014-04-21
After digging into it further, it looks like a lot of the system's files and shared libraries are missing, including /var/backups and /var/dpkg, so the 12.04 is probably unrecoverable unless I run an installer on that partition, in any event I still won't have the package list if I do that. Looks like it's trashed. Unless anyone has any ideas, I'll supply you with any logs you need provided they aren't missing or damaged.

---

