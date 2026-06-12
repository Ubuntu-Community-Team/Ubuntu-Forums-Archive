---
title: "Smooth boot, no grub?"
date: 2008-03-24
forum: General Help
---

### Post by itendsnow on 2008-03-24
My laptop is Ubuntu only, and basically after my inital Vaio boot screen I just want it to go into booting ubuntu with no wait time, I can fix grub with a live cd if need be I just want a smooth transistion.

How would I acheive this?

---

### Post by Oldsoldier2003 on 2008-03-24
> **itendsnow said:**
> My laptop is Ubuntu only, and basically after my inital Vaio boot screen I just want it to go into booting ubuntu with no wait time, I can fix grub with a live cd if need be I just want a smooth transistion.

How would I acheive this?

edit /boot/grub/menu.lst:

```
timeout		0
```

---

### Post by itendsnow on 2008-03-24
Thanks very much :)

---

