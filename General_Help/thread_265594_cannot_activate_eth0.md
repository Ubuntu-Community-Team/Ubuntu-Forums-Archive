---
title: "cannot activate eth0"
date: 2006-09-26
forum: General Help
---

### Post by awnjoor on 2006-09-26
hi, 

Im having problem with my network cards, I cannot activate them. I dont see any of my network interfaces in the ifconfig output. When i do ifup eth0 or eth1, the message "interface eth0/1 is already configured" always comes. But if i change my /etc/network/interface for eth0 from dhcp to static, eth0 is shown in ifconfig. Please let me know if you need more information. 

tnx

---

### Post by az on 2006-09-26
To what are they connected?

Are you connected to a router, cable modem or ADSL modem?

To configure a network connection to an adsl modem, run

sudo pppoeconf

---

### Post by awnjoor on 2006-09-26
only 1 is connected, its connected to a router

EDIT:
meh, somehow i uninstalled dhcp-client from my computer, i installed it back and everything is back to normal.

---

