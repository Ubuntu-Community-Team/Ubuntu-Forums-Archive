---
title: "RAID - GUI/CLi (Repair)"
date: 2007-07-16
forum: General Help
---

### Post by workaholicbe on 2007-07-16
Hi all,

I'm having trouble with a RAID 5 Container...sometimes the RAID boots in a normal way. Sometimes he gives me the finger and says:" I won't boot for you"

At Bootup of my server, it always gives me the following message :

> Following containers have missing members and are degraded :
Container#1 RAID-5

Followed with the message :
RAID 5 status : Critical

Normally you could repair the thing starting the Configuration Utility (CTRL+A)... and do a restore of the RAID-5. But in this case...if you try to do that. Nothing happens, except a reboot of the machine.

So my question is... is there a kind of GUI/CLI tool for (K)ubuntu which i can repair the Container without losing data? Is there perhaps a bootable CD/floppy who's able to reconfigure that critical RAID [Heard something about webmin... but can i repair a RAID with that?]

Config :

Dell Poweredge 2500 Server (yeah, it's an old one...i know)
PERC /3 (Container 0)
RAID 5 (Container 1)

---

