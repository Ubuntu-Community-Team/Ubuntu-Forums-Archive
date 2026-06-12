---
title: "Ubuntu server rearrange boot startup"
date: 2018-07-29
forum: General Help
---

### Post by rt400 on 2018-07-29
HI.
I have a UBUNTU 18.0 server with an additional PLASMA GUI interface.
How can I arrange the services and choose who will come first?
I have a DNS service and it constantly fails because the network service comes up with it.
Would appreciate help. Thanks.


I'm familiar with UBUNTU but not really an expert, you might say an advanced beginner.

---

### Post by SeijiSensei on 2018-07-29
You're not trying to use wifi, right?  If so, the network connection is not made until after someone logs in.  You need to use a full-time wired Ethernet connection if you want to run a server.

If you are using Ethernet, then you shouldn't see this problem because the DNS server, BIND9, isn't started until after the network comes up.

---

