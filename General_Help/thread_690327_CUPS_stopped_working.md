---
title: "CUPS stopped working"
date: 2008-02-07
forum: General Help
---

### Post by merike on 2008-02-07
I had my CanonS100 configured for printing over samba, but today I needed to use it connected directly to my laptop so I added it as an USB printer as well. And it doesn't work at all even though CUPS reports that my jobs are completed:
From dmesg I get:
```
[ 1231.168000] audit(1202396248.480:6):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=6458 profile="/usr/sbin/cupsd"
[ 1243.948000] audit(1202396261.481:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=6476 profile="/usr/sbin/cupsd"
```

Edit: Removing the printer from CUPS and adding it again helped.

---

