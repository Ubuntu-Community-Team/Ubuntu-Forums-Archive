---
title: "possible typo in recent 12.04 security updates broke virtualbox"
date: 2013-12-31
forum: General Help
---

### Post by philip-clifford on 2013-12-31
Virtualbox gui has stopped working for me in the last couple of days and it looks like a typo has crept into libgssapi, as the following error appears on my fully-updated 12.04 LTS (with any de-install/re-install of ubuntu repository virtualbox or Oracle repository virtualbox 4.3.6. 4.3.4 ... > VirtualBox: Error -610 in supR3HardenedMainInitRuntime!VirtualBox: dlopen("/usr/lib/virtualbox/VBoxRT.so",) failed: /usr/lib/x86_64-linux-gnu/libgssapi.so.3: symbol krb5_free_tisket, version HEIMDAL_KRB5_2.0 not defined in file libkrb5.so.26 with link time referencejust guessing that should be krb5_free_ticket

---

### Post by oldos2er on 2013-12-31
You should probably file a bug against libgssapi. ```
ubuntu-bug libgssapi
```

---

### Post by philip-clifford on 2013-12-31
Thanks Ann,
I was heading down that route, but after a reboot all is working again so just have to chalk it up to the machines wanting to mess with my head on new year's eve. Have a brilliant 2014.

---

