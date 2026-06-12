---
title: "Firestarter logs all event Directions as Unknown, making Outbound policies impossible"
date: 2007-01-09
forum: General Help
---

### Post by michael_a on 2007-01-09
I've recently tried Firestarter firewall on two different machines with Ubuntu installed, and for some bizarre reason which i've never encountered with Debian before Firestarter can't seem to discern whether the direction of traffic is Inbound or Outbound, instead listing the direction as Unkown in the event log. On top of this all events appear to be treated as Inbound, so you cannot easily create Outbound policies without doing so manually. 

I'm uncertain as to whether this is a product of something within the Ubuntu environment, or if it might just be a problem in the latest Firestarter release. I have other Debian machines on the network running Firestarter without problems, but they are not running the same version.

I have sent an email to the Firestarter maintainers, but I'm unaware of any more specific forum, and the Firestarter docs make no mention of this Unknown status, which is why I decided to request support from this forum. I imagine it is quite likely that Firestarter is simply relaying this status from sub-utilities such as iptables, but nevertheless this is the context of this dilemma for which i'm seeking remedy or at the least any ideas anyone might share.

sincerely,

michael

---

