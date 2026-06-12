---
title: "CUPS UDP Flood?"
date: 2007-01-22
forum: General Help
---

### Post by The_Major on 2007-01-22
My setup is a Kubuntu (Edgy) desktop behind a hardware firewall sharing files and an Epson printer via samba and cups respectively to 2 laptops running xp and ubuntu. The one laptop has comodo firewall installed as it is wireless. While looking through the Comodo logs this evening, I noticed a UDP packet being sent every 30 seconds or so from the desktop on port 631. Is this normal CUPS behaviour or do I have a problem?

Thanks in advance for your help.

---

### Post by The_Major on 2007-01-23
Anyone have any ideas?

---

### Post by The_Major on 2007-01-26
Bump!

---

### Post by quetzltd on 2008-05-26
Looks like it is normal CUPS behaviour. It announces the shared printers to the local broadcast address on that UDP port (631)(this is used as both source and destination port). This is controlled with the command *Browsing On* in *cupsd.conf*. This in theory allows you to add clients with cups enabled that will automagically discover the cups server and printers that are configured on the server and add them to your local configuration without any human intervention. 

That said, a lot of firewall configs then go and break this by refusing the incoming broadcast, thereby forcing a Firewall rule change or manual configuration of the printers on each client cups configuration.

Keith

---

