---
title: "eth0 restarts itself"
date: 2007-07-28
forum: General Help
---

### Post by brad.m.sims on 2007-07-28
It will shut itself off and back on, kicking me off line in irc...

I see nothing in the logs, other than the message that it did so...

I have tried telling it to use dhcp, not use dhcp, and closing and not closing Knetwork Manager...

This just started today... any help? no one in the irc channel had any ideas

---

### Post by brad.m.sims on 2007-07-29
FIXED!!!!

I had  both libavahi-core4 and libavahi-core5 installed.

Getting rid of libavahi-core4 fixed the problem.

---

