---
title: "Can't partition usb flash drive due to ubunu auto-mounting halfway through"
date: 2006-12-28
forum: General Help
---

### Post by Dave54 on 2006-12-28
I'm trying to partition my usb flash drive with gparted. I can unmount it and delete partitions, but as soon as I try to make a new partition, ubuntu auto-mounts it in the middle of making the partition. Can anyone help?

Thanks,
-Dave

---

### Post by brownkenny on 2006-12-28
Go to System -> Preferences -> Removable Drives and Media.  Under the "Storage" tab, deselect the "Mount removable drives when hot-plugged" box.  It should be the first one under "Removable Storage."

---

### Post by Dave54 on 2006-12-28
Worked perfectly. Thank-you.

---

