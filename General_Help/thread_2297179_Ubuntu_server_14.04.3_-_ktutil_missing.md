---
title: "Ubuntu server 14.04.3 - ktutil missing"
date: 2015-10-01
forum: General Help
---

### Post by tim135 on 2015-10-01
Hi everyone,

For some reason **ktutil** is missing from my Ubuntu Server 14.04.3, when I type in **ktutil** terminal says **command not found**; and when I type in **man ktutil**, terminal says **No manual entry for ktutil**. For that matter I have also tried doing ```
apt-get install ktutil
```, no luck either. What should I do to get it back?

Thanks!

---

### Post by steeldriver on 2015-10-01
It appears to be part of the krb5-user (Kerberos userland) package

---

### Post by tim135 on 2015-10-01
Thanks Steeldriver,
```
apt-get install krb5-user
``` worked perfectly!

---

