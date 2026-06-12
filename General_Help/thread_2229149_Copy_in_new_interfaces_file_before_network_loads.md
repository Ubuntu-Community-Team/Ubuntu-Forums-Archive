---
title: "Copy in new interfaces file before network loads"
date: 2014-06-11
forum: General Help
---

### Post by Mike_Soultanian on 2014-06-11
I have an Ubuntu Live USB installation that will be deployed on hundreds of clients.  It will require a custom interfaces file, but unfortunately it cannot by symlinked to another location (drive is fat32) and it cannot be pre-populated before I create the Live USB image because the hardware differs.

So, what I need to is intervene at some point during boot process, preferably before the network boots and run a special script that builds a custom interfaces file and copies the new interfaces file to the default location.  Is that possible?

Thanks!
Mike

---

### Post by Mike_Soultanian on 2014-06-11
Otherwise, I guess I could just wait until after boot, run the script, copy the new interfaces to /etc/network and then do an ifdown --all and then an ifup --all.  Would that accomplish the same thing?

Thanks!
Mike

---

