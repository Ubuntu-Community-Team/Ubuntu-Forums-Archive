---
title: "Unwanted icon after fstab mount"
date: 2007-01-04
forum: General Help
---

### Post by gladelson on 2007-01-04
I have made a linear array (JBOD) with mdadm (/dev/md0) that I mount on /mnt/share and then export with Samba. I added this line to fstab so that this auto mounts at boot time:
/dev/md0  /mnt/share  ext3  rw,user  0  0

This seems to work but this puts an icon labeled "share" on my desktop automatically. I would rather this icon not be there. Is there a way to prevent this?

---

