---
title: "Drives on desktop"
date: 2006-11-01
forum: General Help
---

### Post by paparucino on 2006-11-01
Hi guys,
may be this is a faq, if so, pardon me.
On my desktop there are the icons of 8 drives/partitions. How can I  remove them since I like to have a clean, a really clean, desktop.

Thank you in advance

---

### Post by Ramses de Norre on 2006-11-01
```
gconf-editor /apps/nautilus/desktop
```
And uncheck "volumes_visible".

---

### Post by paparucino on 2006-11-01
> **Ramses de Norre said:**
> ```
gconf-editor /apps/nautilus/desktop
```
And uncheck "volumes_visible".

it works! thank you very much

---

