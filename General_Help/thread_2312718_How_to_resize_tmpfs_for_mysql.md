---
title: "How to resize tmpfs for mysql"
date: 2016-02-06
forum: General Help
---

### Post by pactaman on 2016-02-06
How can I quickly resize tmpfs mount that is used for mysql? It was done improperly and an incorrect size was set(needs to be 4GB). Also, the Filesystem doesn't look correct?
> 
Filesystem      Size  Used Avail Use% Mounted on
size=8G          32G  2.4G   30G   8% /var/lib/mysql

mount
size=8G on /var/lib/mysql type tmpfs (rw,relatime)

---

