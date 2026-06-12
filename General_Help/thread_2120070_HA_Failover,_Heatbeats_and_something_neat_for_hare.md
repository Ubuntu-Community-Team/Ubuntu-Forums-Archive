---
title: "HA Failover, Heatbeats and something neat for haresources"
date: 2013-02-25
forum: General Help
---

### Post by Mogsy on 2013-02-25
Hi Guys,

First post so be gentle as I'm a bit of a linux/ Ubuntu noob. 

However the good news is I've managed to setup a HA pair of SIP SBC's running on Ubunutu.

However to complete the illusion i need to make either of the pair look like they are sending from the Shared VIP when they own the VIP.
I was going to do this by via an 'IP route change' command e.g:

ip route change 192.168.70.0/24 dev eth1 proto kernel src 192.168.70.52

(192.168.70.52 being the vip in question)

but the only method i seem to have available is to make some sort of init file that i can have the /etc/ha.d/haresources file start or stop when fail over occurs to update the routes.

its either so simple there is no documentation out there or its just the wrong thing to do. Does anyone have any suggestion on how i can achieve this?

I've had a look at pacemaker but is seem like a bit of over kill for what I'm looking to solve right here.

Thanks in advance for any advice.

Cheers

Rob (Mogsy)

---

### Post by mckenna1977 on 2013-02-25
Have a look at step 04 on this site : [https://wiki.archlinux.org/index.php/Simple_IP_Failover_with_Heartbeat](https://wiki.archlinux.org/index.php/Simple_IP_Failover_with_Heartbeat)

It looks like you associate the VIP with the service you're using Heartbeat to monitor. Externally the VIP should respond (though the actual IP should also respond).

---

