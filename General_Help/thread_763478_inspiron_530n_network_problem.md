---
title: "inspiron 530n network problem"
date: 2008-04-23
forum: General Help
---

### Post by voland66 on 2008-04-23
Hi,
I just got Inspiron 530n and immediately encountered a strange networking problem.

I am trying to connect to wired office network -- either using static IP or dhcp. With the static IP I am unable to even ping the gateway. With dhcp I get a message along the lines: "no dhcp lease offers received" (the network router does have a record of a lease to my mac address -- for with a length of a couple of minutes only; other machines have leases for an hour; in addition a couple of lines in the lease records are missing compared to other lease records). So, no connection.
I only had a quick look -- a network card is using e1000 module, I believe.

However, if I instead connect a linksys router to the office network and then connect the desktop to the router, everything works. Desktop happily receives 192.168.1.x IP from the linksys, linksys gets lan address from the network, and the desktop can connect to the web.

This workaround will work for a while, but it is really clumsy -- any ideas as to what can be going wrong in trying to connect to the wired office network?

Thanks,
Yuri

---

