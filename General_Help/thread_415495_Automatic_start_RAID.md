---
title: "Automatic start RAID"
date: 2007-04-20
forum: General Help
---

### Post by greenmeat on 2007-04-20
Here is my problem.

I expanded my root Volume Group to include a new RAID array, /dev/md2.

But I forgot to added it to /etc/mdadm/mdadm.conf. So now the system refuses to boot because the root VG will not start without /dev/md2 started first.

So how can I make /dev/md2 start at boot time now?

Please advise.

---

