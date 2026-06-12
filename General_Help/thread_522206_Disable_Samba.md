---
title: "Disable Samba"
date: 2007-08-10
forum: General Help
---

### Post by BruceWilkinson on 2007-08-10
How do I turn off or disable Samba. I don't want staff Windows workstations/servers visible to public Linux computers.

Bruce

---

### Post by wjp.reg on 2007-08-10
you can uninstall samba using synaptic.

you can stop it with the following command:

```
sudo /etc/init.d/samba stop
```

---

### Post by BruceWilkinson on 2007-08-14
That leads to a follow up question, will that only stop it until a new user logs on, or till the system is restarted? I don't want Samba to run at all.

Bruce

---

### Post by wieman01 on 2007-08-14
> **BruceWilkinson said:**
> That leads to a follow up question, will that only stop it until a new user logs on, or till the system is restarted? I don't want Samba to run at all.

Bruce
Simply uninstall it via Synaptic. That's the best option for you.

---

