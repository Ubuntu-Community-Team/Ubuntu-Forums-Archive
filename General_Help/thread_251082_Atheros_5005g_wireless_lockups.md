---
title: "Atheros 5005g wireless lockups"
date: 2006-09-04
forum: General Help
---

### Post by xaos5 on 2006-09-04
I have an atheros 5005g card and have somewhat of an annoying problem. Ubuntu detects my card right but loads the drivers wrong. I found a script online that allows it to work right.

```

#! /bin/sh
rmmod ath_pci
rmmod ath_rate_sample
rmmod ath_hal
rmmod wlan
modprobe ath_pci
iwconfig ath0 up
iwlist ath0 scan
exit
```

How do I blacklist these modules from loading on startup?

---

### Post by xaos5 on 2006-09-06
bump

---

