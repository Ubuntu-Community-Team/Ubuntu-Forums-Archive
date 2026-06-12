---
title: "Hibernate corrupts swap partition"
date: 2007-04-09
forum: General Help
---

### Post by wj32 on 2007-04-09
Whenever I try and hibernate, my swap partition gets corrupted and it doesn't resume. Just starts up normally (without swap). Any ideas why?

---

### Post by heimo on 2007-04-09
I don't have much experience with this stuff, but I can point you to check /var/log/messages for any errors/warnings that might give you idea what's going on. Is your swap partition at least 1,5 times your RAM?

---

