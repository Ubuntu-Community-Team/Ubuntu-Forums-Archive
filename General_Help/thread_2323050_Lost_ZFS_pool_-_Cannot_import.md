---
title: "Lost ZFS pool - Cannot import"
date: 2016-05-02
forum: General Help
---

### Post by Gridwalker on 2016-05-02
Hi there,

I have just lost a 4 disk Raid-Z partition and I can find no way of getting it back.

It is composed of 4 2tb disks (SDC/D/E/F) and it literally just vanished after a reboot.

The pool was called Oodako (following my Kaiju based naming scheme) ...

I have tried importing the old config using *sudo zpool import -f Oodako* but it simply reports "no such pool available"

*sudo zpool import -f* reports "no pools available to import"
*sudo zpool history* reports "no pools available"
*sudo zpool online Oodako* reports "missing device name"
*sudo zpool online Oodako sdc1 sdd1 cde1 sdf1* reports "cannot open 'Oodako': no such pool"

Will recreating the pool destroy all data? Is there any way to rebuild the pool without needing to import it?

---

### Post by lukeiamyourfather on 2016-05-11
If you create another pool it will destroy all data on the drives. Try this command to simply list what pool are available to import but not actually try to import them.

```
sudo zpool import
```

---

