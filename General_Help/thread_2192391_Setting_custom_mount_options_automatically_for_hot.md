---
title: "Setting custom mount options automatically for hotplug ntfs partition"
date: 2013-12-07
forum: General Help
---

### Post by Lars Noodén on 2013-12-07
I have an external drive formatted to ntfs (for test purposes) that gets mounted automatically with the options rw,nosuid,nodev,allow_other,default_permissions,blksize=4096

What I am looking for a way to do is to have that drive mount with different options, but still automatically mount.  The options I am looking to add are "dmask=022,fmask=133"  How can these automatic mount options be changed for a single drive?

---

