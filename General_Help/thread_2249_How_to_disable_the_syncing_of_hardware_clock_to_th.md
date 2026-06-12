---
title: "How to disable the syncing of hardware clock to the internet?"
date: 2004-10-26
forum: General Help
---

### Post by HiddenWolf on 2004-10-26
How can I disable the syncing of the hardware clock to the ubuntu timeserver?

It is something I don't want, have never had any problems with my clock

on top of that, it tries to sync before it brings my (non-functional as of yet) ppp0 connection up, so it will always time out.

---

### Post by HiddenWolf on 2004-10-26
Damn, Will try rc-update...

Sorry

---

### Post by shufla on 2004-10-27
Hello,

But  AFAIR rc-update.d is overriden by update of system :( Put line ```
exit 0
``` in file /etc/init.d/ntpdate (or similar) on the top, under #!/bin/sh

Best regards,
Lukasz Nowak

---

