---
title: "partition uuid"
date: 2007-06-01
forum: General Help
---

### Post by Gagle on 2007-06-01
Hi,

While repartitioning the hdd of an old laptop running Edgy , the new partitions weren't attributed uuid .'
The parition with the boot flag is OK, but the swap is without uuid.
Also, Edgy's fstab file uses the uuid to locate the partition instead of using the /dev/XXX identifier.

How can I make my computer attribute an uuid to my swap partition ?

gagle

---

### Post by Gagle on 2007-06-01
Never mind.  mkswap did the job.

Sorry for wasting this server's processing power and time and thanks to all those who keeps the great documentation out there !

regards,

gagle

---

