---
title: "How to edit registry by chntpw?"
date: 2024-09-07
forum: General Help
---

### Post by mangada on 2024-09-07
There many articles on deleting password using **chntpw,** but another function of **chntpw** is editing the registry, how can I use it?

---

### Post by jeremy31 on 2024-09-07
You mount the Windows system drive in Ubuntu, then in terminal cd into /[MountedDrive]/Windows/System32/config and then run ```
chntpw -e SYSTEM
```

---

### Post by mangada on 2024-09-12
> **jeremy31 said:**
> You mount the Windows system drive in Ubuntu, then in terminal cd into /[MountedDrive]/Windows/System32/config and then run ```
chntpw -e SYSTEM
```  Is ```
chntpw -e SOFTWARE
``` another branch of registry?

---

