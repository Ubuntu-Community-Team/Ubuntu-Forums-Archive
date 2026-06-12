---
title: "Cat /var/log/thttpd.log (auto refresh?)"
date: 2007-08-05
forum: General Help
---

### Post by phillips321 on 2007-08-05
Hi guys,

I regulary ssh into my webserver to monitor the traffic, i simply like to watch /var/logs/thttpd.log.

The way i watch it currently is to simply:
```
cat /var/logs/thttpd.log
```

Is there a way i can automatically refresh this output? Or any other way i can do this?

Cheers

---

### Post by nitro_n2o on 2007-08-05
```
tail -f /var/logs/thttpd.log
``` this will give what happens on the fly instantly :)

---

### Post by phillips321 on 2007-08-05
jobs a good1, works fine, cheers :)

---

