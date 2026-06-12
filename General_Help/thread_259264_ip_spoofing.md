---
title: "ip spoofing ?"
date: 2006-09-17
forum: General Help
---

### Post by deadite66 on 2006-09-17
i had some warnings from the router that ip_spoofing was going on.


> 
Sep 17 08:17:01 192.168.0.1 Sun Sep 17 08:17:13 2006 GamerLounge System Log: Dropped packet from 192.168.88.1 to 64.12.29.72 that was received from the wrong network interface (IP address spoofing)
Sep 17 08:17:02 192.168.0.1 Sun Sep 17 08:17:15 2006 GamerLounge System Log: Dropped packet from 192.168.254.1 to 38.99.76.88 that was received from the wrong network interface (IP address spoofing)
Sep 17 08:17:15 192.168.0.1 Sun Sep 17 08:17:27 2006 GamerLounge System Log: Dropped packet from 192.168.254.1 to 192.168.0.255 that was received from the wrong network interface (IP address spoofing)
Sep 17 08:17:15 192.168.0.1 Sun Sep 17 08:17:27 2006 GamerLounge System Log: Dropped packet from 192.168.88.1 to 192.168.0.255 that was received from the wrong network interface (IP address spoofing)
Sep 17 08:18:42 192.168.0.1 Sun Sep 17 08:18:54 2006 GamerLounge System Log: Blocked outgoing TCP packet from 192.168.0.200:139 to 192.168.88.1:2536 as SYN:ACK received but there is no active connection


lots of that going on.

and this from ntop
[ntop image]("http://ghostpilot.org/titanshare/pictures/moonunit/ntop_spoof.jpg")

just appears to be traffic on netbios-ip.
my samba shares are passworded.

1. could this be a hacking attempt or something generated from my own network (i have no win98 machines)
2. as ntop picked it up it got passed the router anything i can change to block it?

the time it started  (+1 hour) coincide with installing ntop.
something ntop is doing?
i tried uninstalling it but still kept getting the hits on the router. :<

---

### Post by deadite66 on 2006-09-17
think its sorted, uninstalled vmware on windows and the spoof errors stopped.
vmware has been running fine for months without all the errors until yesterday.

---

