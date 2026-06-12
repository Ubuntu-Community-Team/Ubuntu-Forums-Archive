---
title: "chattr +i symlink"
date: 2019-09-20
forum: General Help
---

### Post by Skaperen on 2019-09-20
is there any way to protect a symlink with +i file attributes the same way a regular file can be?

---

### Post by TheFu on 2019-09-21
Use a read-only file system mount?  I use read-only NFS mounts all the time.

---

### Post by Skaperen on 2019-09-21
i've tried that with bind mounts.  it refuses unless the original is also read-only or i drop the read-only from the bind mount.  so i should export it over NFS on localhost and mount *that* read-only?

---

