---
title: "How to make /host read-write only for root?"
date: 2008-05-15
forum: General Help
---

### Post by metchebe on 2008-05-15
Hi

I would like to know if it's possible to make /host read-write only for root, and read-only for everyone else. Basically I want the equivalent of umask=0222, but since the Wubi Ubuntu installation doesn't use fstab for the host partition, I don't know how to do it.

Thanks,
Marco

---

### Post by ago on 2008-05-16
you can pass mount parameters at boot using rootflags=XYZ

---

### Post by metchebe on 2008-05-16
> **ago said:**
> you can pass mount parameters at boot using rootflags=XYZ

Thanks, how would I do that? Could you point me to some reference or tell me what to do? This goes beyond my current linux knowledge.

Thanks,
Marco

---

### Post by ago on 2008-05-17
Append the appropriate boot parameters to the kernel line in /ubuntu/disks/boot/grub/menu.lst

---

