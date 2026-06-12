---
title: "root pw to mount ntfs?"
date: 2008-02-15
forum: General Help
---

### Post by mfaust731 on 2008-02-15
i just added a 500gb ntfs drive, and i must type my pw to mount it everytime.
is there a way to automate this?
im on gutsy btw

---

### Post by Zack McCool on 2008-02-16
The obvious way would be to add it to /etc/fstab

This will mount it on boot, and won't ask for a password.

/dev/sd1 /mnt/mountpoint ntfs-3g defaults 0 0

Of course, make sure you have fuse and ntfs-3g installed first...

---

