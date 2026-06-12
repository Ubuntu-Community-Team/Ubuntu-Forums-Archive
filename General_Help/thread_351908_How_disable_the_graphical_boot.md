---
title: "How disable the graphical boot?"
date: 2007-02-02
forum: General Help
---

### Post by ungluun on 2007-02-02
Hi,

When Ubuntu boots, it shows a splash screen with a progress bar.
It's fancy, but I rather liked the floating text while booting.

How do I disable this splash screen?

Thanks

---

### Post by banditti on 2007-02-02
Remove both "quiet" and "splash" options from the kernel entry in /boot/grub/menu.lst

---

### Post by ungluun on 2007-02-02
Worked like a charm.
Thanks man :).

---

### Post by banditti on 2007-02-03
My pleasure.

---

