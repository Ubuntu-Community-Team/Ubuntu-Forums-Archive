---
title: "Ubuntu 12.04 gateway dhcp issue"
date: 2012-11-20
forum: General Help
---

### Post by esity on 2012-11-20
Hello everyone!

I need a little help. I will explain this the best I can so people don't have to ask extra questions


Essentially, I have a dell poweredge 2650, with 2 nics. eth0 goes to my cable modem, while eth1 goes to a dell powerconnect 3348.

I have installed isc-dhcp-server on my machine also. The goal is for this box to be my dhcp server and my gateway to the magical internet.

Here is my set up for /etc/network/interfaces
auto lo
     iface lo inet loopback

auto eth0
     iface eth0 inet dhcp

auto eth1
     iface eth1 inet static
     address 10.0.1.1
     netmask 255.255.255.0
     network 10.0.1.0
     mtu 1392 

I added the mtu in when i was trouble shooting.

when I type in ifconfig, eth0 has the external address from my comcast cable modem. eth1 is set to 10.0.1.1 like i asked.

When I connect things to the server via the switch/ethernet, an ip address gets assigned between 10.0.1.150 - 10.0.1.199 without any problems

When I try to do anything from my gateway, apt-get update/install it connects and works no problem. 

When I try apt-get from my other boxes, its super slow, like 1% a min or slower. I can't access internet pages via my macbook or hp laptop. 
However I can ping and traceroute not problem.

via mac terminal
ping -s 549 google.com does not work and gets a time out error but
ping -s 548 google.com works fine.


I have no idea why this would be happening and I can't find anything around other then the mtu stuff which I don't understand.


Let me know if you have any questions or ideas.

matt

---

### Post by Kirk Schnable on 2012-11-20
It sounds like you didn't actually do anything to make your gateway do any traffic routing... without instructions to actually route the traffic, it's not going to go anywhere.

You can do this with iptables.

You will need to have packet forwarding enabled in your kernel.

This will do the trick:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

You'll also need to do some NAT.   This should get you up and running.

```
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth1 -j ACCEPT
```

If this works, you will want to apply the routing configuration at boot, which I like to do in a cron script @reboot.  If you want help writing some iptables rules or making a cron script to run at boot, I'd be happy to assist you further with that.

Cheers
Kirk

---

