---
title: "NFS question - /usr/home keeps disappearing!"
date: 2007-09-05
forum: General Help
---

### Post by skullmunky on 2007-09-05
i have a bunch of users served with NIS and NFS.  been doing this for years w/ redhat and suse, now with ubuntu.   works fine, but just discovered this weird thing:

these user home directories are mounted in /usr/home rather than /home (vestigial leftover from sgi days).   in ubuntu there is no /usr/home; i create it, start NFS, everything's fine.  but, whenever i reboot, /usr/home is gone!  weird!  any idea what could cause this?

---

