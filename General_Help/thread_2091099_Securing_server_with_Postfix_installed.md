---
title: "Securing server with Postfix installed"
date: 2012-12-04
forum: General Help
---

### Post by cbillson on 2012-12-04
Hi, pretty much a beginner, so please bear with me.
 
I have an installation of Ubuntu server (specifically required no GUI) installed with the minimum packages etc to get the application working.
 
Part of the install was to minimise the services offered by the box, a couple of the applications however had MTA dependencies.
 
Postfix got installed and up to now i've kept it 'safe' (ish) by not allowing it in/out via the firewall.
 
A couple of the supporting applications however can output via mail and would be extremely useful, so i'd like to be able to secure Postfix to only send mail to certain locations and ideally then use FIM on the configuration to detect and changes to this.
 
Looking on the net, i see Postfix has whitelist / blacklist functionality and appears to work both inbound and outbound.
 
Would anyone be able to assist me with an extremely basic config to do:
 
Allow no external mail in (will keep blocking by the firewall anyway)
Allow outbound mail only to a single specific email address (or) single domain
 
I'm going to have a play with some of the examples this afternoon and see what i can come up with, but any pointers gratefully received 
 
Thanks

---

