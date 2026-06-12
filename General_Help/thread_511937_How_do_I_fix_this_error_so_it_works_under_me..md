---
title: "How do I fix this error so it works under me."
date: 2007-07-28
forum: General Help
---

### Post by C4U53 on 2007-07-28
/var/lib/tor is not owned by this user (c4u53, 1000) but by debian-tor (110). 

Sorry for such a newb question.. just annoying.. been looking around for an answer and can't find one

---

### Post by Happy_Man on 2007-07-28
Run the command ```
gksudo nautilus
```

And change the permissions for that folder. Navigate to it, right-click, properties, Permissions, change it to whatever you want.

---

