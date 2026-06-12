---
title: "Protect DNS entries in resolv.conf"
date: 2004-11-01
forum: General Help
---

### Post by chard on 2004-11-01
How can I protect my DNS entries in resolv.conf while still using DHCP?

Does Ubuntu support pump, if so, I'm unable to locate it...


Thanks!

---

### Post by oohlaf on 2004-11-01
You can use resolveconf
```
apt-get install resolveconf
```
which allows you to add the dns options to /etc/network/interfaces.
```

iface eth0 inet dhcp
  dns-search some.domain.org
  dns-nameservers 192.168.1.1

```
.

---

