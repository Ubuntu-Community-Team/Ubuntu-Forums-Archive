---
title: "Why is resolv a listening service? Isn't it dangerous to run a service?"
date: 2022-08-18
forum: General Help
---

### Post by vbgf3 on 2022-08-18
Hi,

Did a netstat -tunlp today and found port 53 is a listening port. Did a little digging around and found it is resolv in /etc/systemd . Isn't running a service dangerous? If so, why is Ubuntu making us run this on a personal machine?

---

### Post by The Cog on 2022-08-18
It listens for name lookup requests from applications. It can't work unless applications can send their requests to it.
But if you look closely, it only listens on 127.0.0.1:53. 127.0.0.1 is the loopback address and it's not accessible from outside - only local applications can talk to it. So it is not a security risk. You will find that many server applications (e.g. databases web servers) only listen on 127.0.0.1 when they are first installed for this reason - you have to configure them to listen on other addresses if you want to offer external services.

---

### Post by vbgf3 on 2022-08-22
Yes, now I see that it is listen on local 127. My mistake.

---

