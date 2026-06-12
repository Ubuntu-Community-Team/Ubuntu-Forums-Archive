---
title: "[SOLVED] network-admin issue"
date: 2008-07-09
forum: General Help
---

### Post by Dunstan on 2008-07-09
I need to rename my computer with "gksudo network-admin"

But get this return:

** (network-admin:2998): CRITICAL **: Unable to lookup session information for process '2998'

followed by a bunch of 'SSSS'.  The network setting manager comes up, but will not allow me to unlock it.  Is this a problem with Hardy?  

TIA

---

### Post by cariboo on 2008-07-09
Just run  the command with out the gksu:

```
network-admin
```

Jim

---

### Post by Dunstan on 2008-07-09
Thanks.  I actually just used the System > Administration menu and it worked.  Don't know why I didn't think of it before!

---

