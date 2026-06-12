---
title: "asus a3h notebook, how to turn wlan off"
date: 2007-12-04
forum: General Help
---

### Post by matthias108 on 2007-12-04
hello,

I want to turn off the wlan device on my notebook. i have tried

ifconfig eth1 down

but it doesnt seem to work.


thanks!

---

### Post by geraldm on 2007-12-04
wireless devices have names like "wlan0" 
find them with /sbin/iwconfig
turn off with
```

/sbin/ifconfig wlan0 down

```

Gerald

---

