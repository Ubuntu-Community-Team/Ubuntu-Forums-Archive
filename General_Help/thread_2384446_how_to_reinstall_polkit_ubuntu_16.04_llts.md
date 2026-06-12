---
title: "how to reinstall polkit ubuntu 16.04 llts?"
date: 2018-02-07
forum: General Help
---

### Post by liutauras on 2018-02-07
how to reinstall polkit ubuntu 16.04 lts?

---

### Post by TheFu on 2018-02-07
```
sudo apt update
sudo apt --reinstall install {polkit-package-for-your-DE}
```

So, I installed MATE, so the polkit-package-for-your-DE is "mate-polkit". If you aren't using MATE, then this isn't likely to be the correct answer for you. Also, there are 5 packages listed with "polkit" in the name here.

```
dpkg -l |grep polkit
``` will provide a list.  -l is "dash el"

---

