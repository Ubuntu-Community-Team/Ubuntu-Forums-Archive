---
title: "starting network problem"
date: 2014-06-08
forum: General Help
---

### Post by jgw on 2014-06-08
When I start my machine I have to manually start the network.  When the machine boots it tells me that its disconnected but, as far as I can tell, never tries to connect.  Anyway, after I go in and click on the connection it whirs for a bit and then asks for my password as it is also starting my vpn (I checked the box to do that).  What I am wondering is if its possible to not only start the network when the system comes up but somehow give it my password so it doesn't ask.  

Thank you..........

---

### Post by fr-andres on 2014-06-08
Hi, maybe some more seasoned people answers you later, but meanwhile you can take a look to this links:
[http://askubuntu.com/questions/258580/how-to-run-a-script-every-time-internet-connects](http://askubuntu.com/questions/258580/how-to-run-a-script-every-time-internet-connects)
[http://superuser.com/questions/671170/start-script-on-network-connect](http://superuser.com/questions/671170/start-script-on-network-connect) (for the script)

If I understood correctly your question, the main idea is to put your password etc into a bash script that runs on startup and automatizes the connection process even before the login.
(I've never done it myself). It is possible because of the different "runlevels" that take part on the startup of the system.
Hope that it helps!
cheers,
Andres

---

### Post by steeldriver on 2014-06-08
It sounds like you have a mix of server-style (/etc/network/interfaces - started at boot time) and desktop-style (NetworkManager - connects when a user logs in) that are not playing together nicely. Can you post the contents of your /etc/network/interfaces and /etc/NetworkManager/NetworkManager.conf files?

---

### Post by jgw on 2014-06-09
thank you for the reply.  As per your requesst:
Interfaces:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

network manager conf:
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=00:E0:4D:C2:89:1A,

[ifupdown]
managed=false

---

