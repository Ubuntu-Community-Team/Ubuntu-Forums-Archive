---
title: "How to add startup script as early as possible in bootup process?"
date: 2014-02-15
forum: General Help
---

### Post by redss on 2014-02-15
I am customizing a liveUSB of Ubuntu 10.04 (not willing to upgrade since it's already heavily customized).  I need a way to have a script run as early as possible during the bootup process, before the DHCP negotiation.  I already found that a script in /etc/NetworkManager/dispatcher.d does not execute as expected during the liveUSB startup process.  

Where can I create such a script?

---

### Post by ian-weisser on 2014-02-16
You must edit the upstart jobs in /etc/init to make networking dependent upon your job.

---

