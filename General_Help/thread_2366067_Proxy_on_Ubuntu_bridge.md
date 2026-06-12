---
title: "Proxy on Ubuntu bridge"
date: 2017-07-13
forum: General Help
---

### Post by fuadk on 2017-07-13
Hi,
I have ubuntu 16.04, and I have installed Bridge using the GUI Network connections, and it is working fine.
Bridge eth0 is connected to internet, and eth1 is connected to LAN.

I have a proxy server, and I have set the proxy using the below commands:

URLF=192.168.1.103:8080
iptables -t nat -A OUTPUT -p tcp --dport 80 -j DNAT --to-destination $URLF
iptables -t nat -A OUTPUT -p tcp --dport 443 -j DNAT --to-destination $URLF

Proxy is working fine if I use the Bridge PC browser.
But PC connected to eth1 traffic does not go through the Proxy, even though it is able to access internet through the bridge.

I also tried to set the Proxy using the GUI Network, and I got the same result.

How can I direct the PC traffic to go through the bridge Proxy?


Regards,
Fuad

---

