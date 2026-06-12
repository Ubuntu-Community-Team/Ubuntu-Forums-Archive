---
title: "[SOLVED] Disable default kubuntu laptop power manager from starting"
date: 2007-08-06
forum: General Help
---

### Post by strabes on 2007-08-06
I have switched to kpowersave because I feel that it's better than the default kubuntu power manager (kde-guidance-powermanager)

How do I disable the default one from starting up with X? I cannot find anything with that name in BUM. Help please!!

---

### Post by sep1318 on 2007-08-06
Try deleting the file that should be in /usr/share/autostart called guidance-power-manager.desktop . I think that should do it.

---

### Post by strabes on 2007-08-06
Sweet, that worked. Thanks! I didn't even think about the root autostart folder.

---

### Post by sep1318 on 2007-08-06
Always glad to help, and doubly glad to when my help works! :)

---

