---
title: "/var/log/auth.log stops recording authentication errors"
date: 2024-02-12
forum: General Help
---

### Post by zzzzhhhh on 2024-02-12
As the title says, `/var/log/auth.log` stops recording  authentication errors. It all began with I accidentally deleting it.  Then I created it using touch command and changed the owner:group to `syslog:adm`. I have had `rsyslog` installed. But it just does not record anything.

 Any idea to fix it? The OS is Ubuntu Server 22.04.3 LTS. Thanks.

---

### Post by zzzzhhhh on 2024-02-13
Solved. Many thanks to telcoM.

---

