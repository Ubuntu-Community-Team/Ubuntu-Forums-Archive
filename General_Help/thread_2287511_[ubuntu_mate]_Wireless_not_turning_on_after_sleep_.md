---
title: "[ubuntu_mate] Wireless not turning on after sleep mode..."
date: 2015-07-20
forum: General Help
---

### Post by Joe_Martin on 2015-07-20
Hello, using ubuntu mate and loving every minute.  Simply the fastest, rock solid version of any linux os I have used.

One problem, occasionally wireless does not activate after sleep mode.  Sometimes it does, other times it does not.

Any thoughts?

Thanks.

One thing I forgot to mention, it's ubuntu mate15.04

---

### Post by QDR06VV9 on 2015-07-20
That has happened to me also, just from time to time.
My fix was to add a line to the /etc/pm/config.d/config
```
gksu pluma /etc/pm/config.d/config
```
Add this line and save
```
SUSPEND_MODULES="iwlwifi"
```
This tells the system that we have a module (a.k.a. driver) that we want to explicitly unload on suspend and reload on resume.
Thanks to chili555
Regards

---

