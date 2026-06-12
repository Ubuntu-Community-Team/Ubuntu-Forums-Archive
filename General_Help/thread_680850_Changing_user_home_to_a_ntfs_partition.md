---
title: "Changing user home to a ntfs partition"
date: 2008-01-28
forum: General Help
---

### Post by WadiJM on 2008-01-28
Hi All! I would like to move my user home to a ntfs partition. Is there a way to do it? What should I edit on /etc/fstab?.

Thanks in advance,
Regards,
Wadi

---

### Post by taurus on 2008-01-28
It is a real bad idea to have your /home on a ntfs filesystem.  Leave /home on an ext3 filesystem (default) and if you need to use that ntfs partition, mount it to somewhere and use it.

---

### Post by WadiJM on 2008-01-28
Ok...

---

