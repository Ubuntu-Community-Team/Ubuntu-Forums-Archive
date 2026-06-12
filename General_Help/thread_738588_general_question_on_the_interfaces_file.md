---
title: "general question on the interfaces file"
date: 2008-03-28
forum: General Help
---

### Post by StOoZ on 2008-03-28
what is this line doing:
> iface eth0 inet dhcp

I've disabled it and it solved me a major problem that I was experiencing in the last couple of weeks\month.
see this for additional info:
[http://ubuntuforums.org/showthread.php?t=698305]("http://ubuntuforums.org/showthread.php?t=698305")

---

### Post by dcstar on 2008-03-28
> **StOoZ said:**
> what is this line doing:
........

It sets you eth0 interface to use DHCP - it means little without the rest of the contents of that file as far as diagnosing any issue with your system.

---

### Post by StOoZ on 2008-03-28
here is the rest of the file :
> auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
#iface eth0 inet dhcp


my problem is solved, as I already mentioned, just wanted to know, why this line caused such a problem.

---

