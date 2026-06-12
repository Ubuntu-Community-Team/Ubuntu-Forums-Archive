---
title: "Networking with vmware-player"
date: 2007-05-18
forum: General Help
---

### Post by benwei on 2007-05-18
Hello,

I am trying to get host-only networking going with vmware-player.  I've installed vmware-player and the accompanying kernel modules, and then I do:

vmware-config-network.pl
modprobe vmmon
modprobe vmnet
vmplayer

But when I try to connect the Ethernet device, I get a popup saying
"Could not get interface flags for vmnet1: No such device.  Failed to connect virtual device Ethernet0"

/dev/vmnet1 definitely exists, and vmware-config-network.pl reports no errors, and even says, "Configuring a host-only network for vmnet1."  I've tried tail-ing /var/log/messages and I see no messages from vmmon or vmnet, either.

Does anybody know what gives?

---

