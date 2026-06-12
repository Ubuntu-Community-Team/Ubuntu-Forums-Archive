---
title: "Junk Modem, Can I DMZ the machine but secure it somehow?"
date: 2014-03-11
forum: General Help
---

### Post by maddogz420 on 2014-03-11
I have the worst modem in the entire world, one of those Zyxel 5100's, and it really has problems forwarding ports. Sometimes the port forward takes, other times it doesnt. I was wondering if there's a relatively simple way to DMZ my ubuntu box, but install some sort of software firewall or something in order to keep it as secure as possible. 


Any tips/ideas? (Other than buy another modem, heh)

---

### Post by TheFu on 2014-03-11
Security needs to be multi-layered.  When 1 part fails, we need to have a backup until the failed portion can be replaced.
My opinion is that NO server should be placed directly on the internet without the protection of a hardware firewall.

Can you put an ubuntu box directly on the internet and not get hacked?  Certainly.
Should you?  Probably not. I wouldn't ever put a desktop there and would create a VM with a router distribution to make the DMZ before putting a nominal Ubuntu server on the internet without almost every port protected.

My signature has links to security articles. This is a very broad subject, so don't expect to be an expert after reading just a few articles. It can take years to learn this stuff, but we all started somewhere.

Honestly, buying a new router will be the best use of your time and money for the next few months, IMHO.

---

### Post by maddogz420 on 2014-03-11
Thanks for your quick reply, I'll do some reading up on it =)

---

