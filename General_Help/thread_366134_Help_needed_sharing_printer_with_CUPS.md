---
title: "Help needed sharing printer with CUPS"
date: 2007-02-20
forum: General Help
---

### Post by drpaul on 2007-02-20
I really need some help. Have looked at lots of old threads and followed former success, but it hasn't worked for me.

I have a Dapper box that has  a printer attached to LPT1. I had it set up with Samba so it can be seen by a laptop running XP. I can print fine from there [connected wireless to LAN] as well as locally.

I have a new laptop on which I have installed Edgy [sick of the XP thing].  It is also connected wirelessly to the LAN. Sees the internet fine; pings others on the LAN fine.

I have tried to set up CUPS on the first box so that the printer will be seen as a network printer by the new laptop.  I now have access on the Dapper box to administer CUPS, and have modified the cupsd.conf file to allow All in several places. I have added an additional printer in CUPS that has the same driver and a URI that starts with ipp:  If I give that ipp the address that is the host name, then I can send a test page from that host, but I get the "busy" message below from the Edgy laptop. If I use the LAN IP address, e.g., 192.168.0.101, CUPS on both machines reports "Network host '192.168.0.101' is busy; will retry in 30 seconds..."

Naturally, nothing ever happens.

I'm out of ideas and really need help. This shouldn't be that hard. :( 

TIA

Paul

---

### Post by drpaul on 2007-03-06
This may be of interest to all who have viewed this.

Finally got the server to see printer requests by putting 

Listen <server ip address>:631
into /etc/cups/cups.d/ports.conf

Then, the other Ubuntu machine on the network could print to the print server by using the URI parallel:/dev/lp0 which is the same URI listed in the server's printer description.

All attempts to use ipp protocol [either from the server or the client]  generated a backend failure.

So the problem seems solved, but not in the ways that the user literature would guide one.:( 

:confused: 

Paul

---

