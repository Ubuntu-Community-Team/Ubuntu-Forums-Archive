---
title: "3 terabyte logical hdd"
date: 2007-03-30
forum: General Help
---

### Post by ddover on 2007-03-30
Does anyone know if ubuntu will support a 3 terabyte logical hdd (4 X 750 Raid system)? I know there is a limit to the size of a hdd a 32 bit operating system can handle.

Thanks

---

### Post by hikaricore on 2007-03-30
Looks like both ext2 and ext3 support way more than 3 terabytes.

[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2) (Max volume size 	16 TiB)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3) (Max volume size 	2TiB &#8211; 32TiB)

However I would never want to run fsck on a 3TB raid. >.<
That would be a long long scan.

I'm not 100% sure however about 32bit hardware and 3 TiB.  I'm pretty sure it could.

---

