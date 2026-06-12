---
title: "Ubuntu Software Center Lags and Crashes"
date: 2016-12-30
forum: General Help
---

### Post by jmk13 on 2016-12-30
My Software Center lags to the point that it won't even display any icons, just ellipses, and now just immediately crashes and closes. Any help would be appreciated, thank you.

Ubuntu 16.04 LTS
Intel Skull Canyon NUC
i7 6770 HQ
Iris Pro 580
16GB DDR4 
256 SSD m.2

---

### Post by howefield on 2016-12-30
Can you confirm that your installation is up to date ?

```
sudo apt update && sudo apt upgrade
```

If that doesn't help try uninstalling the package and reinstalling..

```
sudo apt purge ubuntu-software
```
```
sudo apt install ubuntu-software
```

---

