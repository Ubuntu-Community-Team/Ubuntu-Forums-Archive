---
title: "Port Forwarding quick question"
date: 2015-06-28
forum: General Help
---

### Post by eth0up on 2015-06-28
Hello.When i log into my router it shows my windows pc port forwarding from utorrent. I was wondering how does utorrent actually portforward on my router without actually having my routers password?Also on my linux machine when i run ```
echo 1 > /proc/sys/net/ipv4/ip_forward
``` Is this just port forwarding my machine or in some way sending packets to my router asking it to forward like utorrent did on my windows box.Sorry i'm just a lil confused

---

### Post by lisati on 2015-06-28
It's likely that your router is using some kind of "stateful" [network address translation]("https://en.wikipedia.org/wiki/Network_address_translation"). For example, one way this can work is that when utorrent on your PC sends an outgoing request, your router "knows" that any replies it receives for that request are intended for the machine that sent the request.

---

### Post by efflandt on 2015-06-28
Torrent programs can usually be set to do uPnP which can set up port forwarding on the fly if the router supports it and has that enabled. I think that is what console gamers are looking for when trying to do what they call "open NAT", although, not sure why console games need port forwarding when I do not know of any PC games that do.

When /proc/sys/net/ipv4/ip_forward contains 1, that enables your Linux PC to forward ipv4 IP traffic between its interfaces (if it has more than one) and something uses your PC as default gateway or specific to the network on your other interface. But that routes IP's not ports. Masquerading (NAT) or port forwarding would be done with iptables rules.

---

