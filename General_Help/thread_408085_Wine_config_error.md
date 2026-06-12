---
title: "Wine config error"
date: 2007-04-12
forum: General Help
---

### Post by APGunner on 2007-04-12
Hey im on ubuntu 7.04 and im trying to get wine running on it. I have installed wine but whenever i execute wine config in the terminal it says 
wine: could not load L"c:\\windows\\system32\\config.exe": Module not found
I have been looking for hours trying to find config.exe on google but I can't find it anywhere. Can someone help me out by giving it to me or maybe theres something else thats wrong. I have never had this problem with wine before on other ubuntu versions.

---

### Post by APGunner on 2007-04-12
no one knows what to do?

---

### Post by david_kt on 2007-04-13
Try:

```
winecfg
```

instead.

DK

---

### Post by GexX2 on 2007-04-13
Ya, winecfg is what you're supposed to run. Typing wine config will make wine look for a config.exe to run.

---

