---
title: "Help enable PPTP VPN client Dial on demand"
date: 2008-05-11
forum: General Help
---

### Post by Heaven Knows on 2008-05-11
Dear everyone!

I was able to setup a VPN client PPTP to Windows VPN server
now I want to use that tunnel to "dial on demand" mode, 
Plz help me to configure it, what to edit in /etc/ppp/otions.pptp
and  /etc/ppp/peers/mytunnels?
I use VPN pptp through DSL internet, not a dial up modem

I have read the quote below but not realy understand

> pppd supports bringing a link up when it is needed. This requires that the static routes are already in place, prior to establishing the connection. Hence, it wont help adding them to ip-up. Instead these routes need to be entered in the start script. 

Edit the start script in /etc/init.d/ and add the required networks through route add for the link in question. 

Consider the example, where we have a peer defined in /etc/ppp/peers called peer1. Then, when establishing the link in demand dial mode, we sleep for a bit, then add the static routes in question. 

pppd call peer1 persist demand idle 3600
sleep 2
route add -net 192.168.0.0 netmask 255.255.255.0 ppp0
Here we can not use a parameter for the link (normally $1 in the ip-up and ip-down scripts). We have to make sure the routes are entered for the correct link, since we are in a start script we can be quite certain no other ppp-links have been brought up. Type ifconfig in a console to ensure that the correct interface is used. When using PPPoE it is likely a ppp0 interface already exists. Then, the pppd call command will bring up the next one, ppp1 in this case. Hence, update the start script to reflect the correct interface name. 

Once an IP packet is sent to the router destined for the VPN ppp interface, the link is brought up. After 3600 (the idle option above) seconds of inactivity, the link is brought down anew and it will revert to the behaviour of waiting for a packet to arrive destined for the VPN link. 

thanks very much

---

### Post by Heaven Knows on 2008-05-12
Up
No one can help me?
So sad. :(

---

