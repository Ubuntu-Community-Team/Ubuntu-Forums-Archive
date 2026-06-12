---
title: "boot flag?"
date: 2007-11-09
forum: General Help
---

### Post by Sanity N/A on 2007-11-09
how do i set a boot flag? 
(pci=noapic)

---

### Post by geraldm on 2007-11-10
If you are using grub:
It would go at the end of the line that begins "kernel" in /boot/grub/menu.lst

Back up that file before editing.

Gerald

---

### Post by Sanity N/A on 2007-11-10
thanks, exactly what i was looking for

---

