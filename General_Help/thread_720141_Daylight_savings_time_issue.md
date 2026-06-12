---
title: "Daylight savings time issue"
date: 2008-03-10
forum: General Help
---

### Post by djbon2112 on 2008-03-10
Hey guys, for whatever reason my Gutsy install isn't updating to the new DST correctly. It appears it's jumped 2 hours ahead instead of the normal 1, and it currently says it's 01:41 when it's actually 00:41. Anyone have any advice?

---

### Post by Oldsoldier2003 on 2008-03-10
> **djbon2112 said:**
> Hey guys, for whatever reason my Gutsy install isn't updating to the new DST correctly. It appears it's jumped 2 hours ahead instead of the normal 1, and it currently says it's 01:41 when it's actually 00:41. Anyone have any advice?

```
sudo ntpdate ntp-1.mcs.anl.gov
sudo hwclock --systohc
```

---

