---
title: "squid and directconnect"
date: 2005-03-30
forum: General Help
---

### Post by boop on 2005-03-30
Hello I am currently trying to use squid to share my internet to the other computers in the network. Surfing works fine but DirectConnect does not  ](*,) My short question is simply, is this type of surfing unsupported by Squid?

---

### Post by fdoving on 2005-03-30
[QUOTE=boop]Hello I am currently trying to use squid to share my internet to the other computers in the network. Surfing works fine but DirectConnect does not  ](*,) My short question is simply, is this type of surfing unsupported by Squid?[/QUOTE]
 What you want is MASQUERADING / NAT.. check out a package called 'guidedog'.

Or you could try this, if you've got the correct modules loaded already:

sudo echo 1 > /proc/sys/net/ipv4/ip_forward
sudo iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE


Change ethX to eth0, eth1 or whatever.. depending on your setup. I can recommend guidedog, if you'd like a graphical interface for connection sharing.. 

Then you configure the other computers in your network to use the linux computer as their default gateway.

Enjoy.

---

