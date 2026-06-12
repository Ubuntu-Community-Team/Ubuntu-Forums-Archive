---
title: "gksudo nautilus fails to set permissions"
date: 2007-11-26
forum: General Help
---

### Post by kkathman on 2007-11-26
Opening gksudo nautilus, and then trying to set permission on an entire directory/folder contents seems to fail.

I copied a folder from another drive to a root.root directory. The folder has root.root ownership.I then opened the folder in gksduo nautilus.  I changed the folder ownership to a local user, and set the permissions to create & delete. I clicked the button that said to apply changes to all files within. The settings WERE changed for the folder, but NOT for the files.

Doing a chmod and chown manually did work, so it seems the internals are ok, just the nautilus command.  Any ideas why this is failing?

Thanks,
Kork

---

### Post by nick_h on 2007-11-26
This could be [Bug #94512](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/94512).

---

