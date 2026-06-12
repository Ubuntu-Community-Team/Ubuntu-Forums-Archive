---
title: "How to avoid Multiple versions"
date: 2007-07-31
forum: General Help
---

### Post by barkerkr on 2007-07-31
After updatiing Ubuntu with the included software update GRUB lists all the diffrent versions to boot into. How Do I keep it showing only the ones it was installed with?

---

### Post by merlinus on 2007-07-31
```

gksudo gedit /boot/grub/menu.lst

```

and place a hashmark (#) in front of the kernel lines you do not wish to appear in the grub menu.

-merlin

---

### Post by barkerkr on 2007-07-31
Thank You!

---

