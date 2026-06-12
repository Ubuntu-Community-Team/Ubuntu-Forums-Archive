---
title: "[SOLVED] opening file browser with root"
date: 2008-05-30
forum: General Help
---

### Post by Kinnza on 2008-05-30
hi,
i need to do some editing on a lib that only root has privs too (/var/www)

but when i open the file browser i cannot access it cause only root is priviliged to this lib

so can i somehow run the file browser under root?

---

### Post by dje on 2008-05-30
Press Alt + F2 and type:
```
gksu nautilus /var/www
```

hope that helps,
dje

---

### Post by Kinnza on 2008-05-30
oh thanks!!!!!

---

### Post by jtheb on 2008-05-30
I open the root terminal, insert passwd, then type in nautilus

---

### Post by Kinnza on 2008-05-30
yeah i was looking for the command: nautilus
:D

---

