---
title: "New (Ubuntu 6.10) PC -- need files moved from old (FC4) PC, NO external media allowed"
date: 2007-04-17
forum: General Help
---

### Post by arcoddath on 2007-04-17
New shiny Dell PC up and running with Ubuntu 6.10 on its 2x HDDs.  However, I have about 40Gb of old files to move from my previous PC which had a Fedora Core 4 setup on its 2 HDDs (IDE so can't install 'em in new Dell PC).  How can I best achieve this?  I suspect some sort of ethernet link is required but I don't know how to do it and there seems remarkably little hard info on the net that I can find.  

Anyway, I have :

1x old PC (delia) (2x HDDs, 1 ethernet card, 2 USB ports, Fedora Core 4 installed)
1x new PC (daphne) (2x HDDs, 1 ethernet port, 6 USB ports)
1X Cat5e ethernet crossover cable

I have no usable external devices and no budget for such things.  If it's possible, it has to be done with existing kit and software

How can I best use the above to get the files from delia to daphne? I'm sure someone's done something similar at least once, surely...?

---

### Post by stuporglue on 2007-04-17
Easiest is if you can plug both into a router, then you don't need any special network config. Then you can install an SSH server on Fedora if it's not already installed, then in Ubuntu, use the Places-->Connect to Server menu, and use the Fedora box's IP address as the hostname to connect to, and the Fedora username/password. Then you can drag-and-drop to your heart's content over the network. 

With no router is very similar, but first you configure both comptuers to be on the same network with static IPs. eg. 192.168.0.1 and 192.168.0.2, and with the same subnet mask. Then do the same thing. 

If you can't install SSH on Fedora, post that here as one of the factors in this problem :-)

---

### Post by FluffyElmo on 2007-04-17
The easiest would be to temporarily move the drives from the old PC into the new one. You can just mount the drives, transfer the files quickly and then power down and put the drives back in the old PC.

---

