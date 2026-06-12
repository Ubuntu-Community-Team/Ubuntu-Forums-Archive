---
title: "Powernap and Unicast Wake on Lan"
date: 2017-04-16
forum: General Help
---

### Post by mcensori on 2017-04-16
Hi there, I've recently decided to move to Ubuntu for my storage server. What I am trying to do is autosuspend the server using powernap, then bring it back out of suspend with unicast packets, however I am having a bit of trouble. A few things to note


[LIST]
[*]Under /etc/network/interfaces, the interface is properly set up to be in wol ug mode on boot
[*]I can bring it out of suspend with unicast packets or magic packets when powernap is not active.
[*]When powernap is active only magic packets will bring it out of suspend
[*]I tried to make an executable script at /etc/powernap/ethtool-command to get powernap to set wol ug on the interface
[*]I have tried to change the /usr/share/powernap/powernap-ethtool file itself when the above didn't work to set it to ug instead of just g
[*]While powernap is running, every time I wake from lan and check ethtool the wol setting is set back to g. Even if I set it manually to ug between wake cycles, it's always back to wol g after the next suspend-wake cycle.
[*]The above is true even if I only run the powernapd daemon as opposed to powernap.service, making me think that powernap-ethtool isn't what is causing the problem.
[*]I have tried setting all ports to be monitored in the powernap configuration file as a last ditch attempt which did nothing
[/LIST]

I think that covers everything I've tried. I'd appreciate any advice that anyone could give on how to get this working as I would like. Cheers.

---

