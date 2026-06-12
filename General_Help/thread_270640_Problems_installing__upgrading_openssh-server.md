---
title: "Problems installing / upgrading openssh-server"
date: 2006-10-03
forum: General Help
---

### Post by Myrios on 2006-10-03
Today the update notifier told me that I needed to update openssh-server. When I ran the uptater, the install failed.

Running apt-get update as root with DEBCONF_DEBUG=developer, I got the following data about the problem:

```
debconf (developer): <-- VERSION 2.0
debconf (developer): --> 0 2.0
debconf (developer): <-- GET ssh/use_old_init_script
debconf (developer): --> 10 ssh/use_old_init_script doesn't exist
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a4.2p1-7ubuntu3.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
```

Any idea how I can solve this?

Thanks in advance, folks...

---

