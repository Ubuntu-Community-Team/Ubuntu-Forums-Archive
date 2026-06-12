---
title: "Getting: xrdp_listen_main_loop: listen error, possible port already in use"
date: 2017-04-08
forum: General Help
---

### Post by vbmark on 2017-04-08
I lost the ability to RDP into my Ubuntu box.  When I run "service xrdp status" I get:

[ERROR] xrdp_listen_main_loop: listen error, possible port already in use

Running this returns nothing:

netstat -an | grep "LISTEN " | grep ":3389"

Nothing seems to be using this port.  I am at a loss.  Any ideas?

Thank you.

---

