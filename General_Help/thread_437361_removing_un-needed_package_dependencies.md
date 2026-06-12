---
title: "removing un-needed package dependencies"
date: 2007-05-08
forum: General Help
---

### Post by residualbit on 2007-05-08
just wondering how to do this...for example, i installed "sql-ledger" then later i decided i did not need it, on install (in package manager) it installed a ton of packages it depended on, but on removal it only removed "sql ledger"

---

### Post by aysiu on 2007-05-08
```
sudo apt-get autoremove
``` or ```
sudo apt-get install gtkorphan gksu
gksudo gtkorphan
```

---

