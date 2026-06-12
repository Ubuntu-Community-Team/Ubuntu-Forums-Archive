---
title: "NTFS issues"
date: 2007-04-22
forum: General Help
---

### Post by Phineas on 2007-04-22
Feisty had immediately recognized the parititons and mounted them but I only have read access.

I have installed ntfs-config, it only allows me to check the latter box concerning external drives, the first box is whited out.

I have installed ntfs-3g to no avail.

I have installed fuse to no avail.

Any ideas on what I need to do?

---

### Post by raja on 2007-04-22
Can you post your /etc/fstab?

---

### Post by Phineas on 2007-04-22
Well turns out it was much simpler than I thought. I solved the problems.

I rebooted the system, unmounted both of my NTFS partitions. Then with NTFS-Config remounted them and it allowed me to tick the checkbox for internal drives.

W00t, victory is mine.

---

