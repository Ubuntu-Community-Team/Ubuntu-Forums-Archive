---
title: "Help creating a script in init.d"
date: 2006-07-17
forum: General Help
---

### Post by speedsix on 2006-07-17
Hi, I basically want to run the following command on boot, it needs to run as root but I don't know what to put at the first part of the command to make it do so? I don't need any fancy start/stop sections in the script, just want to run the following command as root.
```

lircd --connect=10.0.0.4

```


Many thanks

---

### Post by caserio on 2006-07-17
Hi,

Did you try this ?:

##script-foo
#!/bin/sh
lircd --connect=10.0.0.4
##

Put script-foo in the /etc/init.d/ directory

Then sudo chmod 755 script-foo

And sudo update-rc.d script-foo defaults

Don't know if '/sbin/lircd' is required. Try that if it doesn't work.

---

### Post by nleachman on 2006-10-12
Thanks for posting these instructions - they worked great for me!
- Nick

---

