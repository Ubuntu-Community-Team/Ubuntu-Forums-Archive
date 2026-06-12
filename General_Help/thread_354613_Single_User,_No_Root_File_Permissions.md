---
title: "Single User, No Root File Permissions?"
date: 2007-02-06
forum: General Help
---

### Post by Pipistrelle on 2007-02-06
I've been trying to access some configuration files that I'd like to edit, but they're all read-only. When I go to the permissions tab in properties, I'm informed that I am "not the owner and can't change any permissions." I set up a single account when I installed Edgy, so now I'm confused. I made myself a part of the root user group but that hasn't changed anything. Is there anything else I can do?

thanks,
Teresa:confused:

---

### Post by Dr Small on 2007-02-06
Applications -> Accessories -> Terminal
```
gksudo nautilus
```

Dr Small

---

### Post by Ramses de Norre on 2007-02-06
Read [this](http://wiki.ubuntu.com/RootSudo) for more info about ubuntu's sudo system for root privileges.

---

### Post by Pipistrelle on 2007-02-06
Thanks; I'll try the code and read up. I appreciate it.

Teresa

---

