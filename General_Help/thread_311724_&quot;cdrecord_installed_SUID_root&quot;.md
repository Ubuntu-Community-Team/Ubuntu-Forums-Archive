---
title: "&quot;cdrecord installed SUID root?&quot;"
date: 2006-12-03
forum: General Help
---

### Post by Jimmey on 2006-12-03
I get:

> Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?

When trying to write a .iso to a CD. Normal writing works okay. What should I do?

Thanks.

EDIT:

Solved. > sudo apt-get --purge remove cdrecord; sudo apt-get install cdrecord

---

