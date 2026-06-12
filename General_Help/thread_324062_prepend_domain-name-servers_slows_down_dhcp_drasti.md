---
title: "prepend domain-name-servers slows down dhcp drastically"
date: 2006-12-23
forum: General Help
---

### Post by muxecoid on 2006-12-23
If I do not write
```
prepend domain-name-servers correct_dns
```
in dhclient.conf something overwrites correct DNSes with ```
192.168.101.101, 192.168.101.102 
``` **** to leases and resolv. If I do add this prepend it takes minutes instead of seconds to connect to ISP.

Is it possible to set correct DNS once and absolutely prohibit to dhclient to overwrite anything? What is the source and the meaning of 192.168.101.101, 192.168.101.102?

If I can't set static DNS in resolv how do I make prepend faster? And, BTW with supersede instead of prepend it does not connect at all.

---

### Post by muxecoid on 2007-01-03
Who knows?

---

