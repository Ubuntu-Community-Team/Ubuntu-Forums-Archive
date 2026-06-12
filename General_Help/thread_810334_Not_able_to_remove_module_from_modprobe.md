---
title: "Not able to remove module from modprobe"
date: 2008-05-28
forum: General Help
---

### Post by Gorgamel on 2008-05-28
When I tried to remove irda from modprobe, it gives error
```
FATAL: Module irda is in use.
```

I have tried to find some help on zeGoogle, but not helping.
I have also tried to put it in the blacklist, but not working there either.

---

### Post by bingoUV on 2008-05-28
run lsmod. It will show which other module is using irda, and try removing that module first. You will likely see something like
[code]
irda                <dependentModule1 dependentModule2 ...>

remove dependentModule1, dependentModule2 etc, and then try removing irda.

---

### Post by Gorgamel on 2008-05-29
Thanks, helped a lot :)

---

