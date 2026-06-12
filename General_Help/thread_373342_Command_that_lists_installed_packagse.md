---
title: "Command that lists installed packagse?"
date: 2007-03-01
forum: General Help
---

### Post by TheForkOfJustice on 2007-03-01
What command do you enter in terminal that lists the names of all of the installed packages?

---

### Post by yopnono on 2007-03-01
dpkg -l ?

---

### Post by TheForkOfJustice on 2007-03-01
> **yopnono said:**
> dpkg -l ?

Yep, that works.  I also found this:

```

dpkg --get-selections | grep -v deinstall > ubuntu-files
```

---

