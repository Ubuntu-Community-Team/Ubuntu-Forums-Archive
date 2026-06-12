---
title: "[SOLVED] Automount SATA NTFS harddisk (Gutsy)"
date: 2008-03-23
forum: General Help
---

### Post by Blazed on 2008-03-23
Hi all,

Sorry if this question is already answered but searching with google and the forum search engine has not been fruitful.

I have my gutsy partition installed on an external usb drive. I have two internal SATA drives. The first disk contains my vista partition, the second disk data. The first disk (sda) automounts when booting but the second disk (sdb) not. I have to manually mount it after booting and enter my password. :confused:

How can I set both disks to automount?

---

### Post by Blazed on 2008-03-23
Okay, so I ran

```
blkid /dev/sdb1
```

from which I discovered that the UUID in my fstab was incorrect. Changing and rebooting and all is in order! :)

---

