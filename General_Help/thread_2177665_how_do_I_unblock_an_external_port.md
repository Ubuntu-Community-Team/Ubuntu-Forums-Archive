---
title: "how do I unblock an external port?"
date: 2013-09-29
forum: General Help
---

### Post by Kojak Peg on 2013-09-29
Hi Everyone
As the title asked, how do you unblock an external port?

I'm trying to set up Plex to stream content from my computer to my tv, but all my ports are blocked and Plex can't connect to my server and I'm pretty certain it's my ports. I have deactivated my firewall but still nothing

I've got the default firewall (inactive) and firestarter. I am beginning to wonder if I may have installed another firewall program ages ago to try out and have forgotten about it. So could you also give a list of any other firewall programs besides the default one and firestarter 

Thank

---

### Post by HiImTye on 2013-09-29
in Linux, the firewall is in the kernel (netfilter/iptables), not loaded as a program. Firestarter is a GUI front-end.
if I want to open a port, I use [UFW]("https://help.ubuntu.com/community/UFW"), as I prefer the CLI method (and it's a hassle going through iptables, that's typically a last resort if something isn't working).

of course, you will need to open the port on your router, too (or set your Linux box as a DMZ).

---

### Post by 3rdalbum on 2013-09-29
If the firewall on the server is allowing all connections, and the firewall on the client is allowing all connections, then there's no firewall problem. You don't "open a port", you simply run a program that transmits or receives on that port and make sure your firewalls aren't blocking the port.

Firestarter (please, people; stop using it!), UFW and pretty much every other "firewall" program out there on Linux will just configure the internal netfilter/IPtables firewall. If you change the settings on one "firewall" you change it for all.

---

### Post by Kojak Peg on 2013-09-30
Thanks guys, maybe it isn't the firewall that was just my best guess as to what was causing the problem. When I test my ports it comes back with a blocked or timed out message which is obviously what is stopping my from using Plexapp but I am just not familiar with linux to be able to fix the problem. In fact I barely understand the problem in the first place 

why is it timing out and how can I fix it?

is it something my ISP would have to fix or is it an error at my end

Update I fixed the problem with port forwarding I don't know if there is another solution but the port forwarding solution works for more info on port forwarding I found this website [http://portforward.com/](http://portforward.com/)

I would mark the thread as solved but can't find the solved option

---

