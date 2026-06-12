---
title: "IPTABLES - drop traffic arriving at one interface from another."
date: 2015-04-29
forum: General Help
---

### Post by dozy on 2015-04-29
Hey Everyone,

Thanks for taking the time to read this.
I am trying my hand at writing my own firewall using iptables, but I have come across a situation that I cannot solve on my own.

I will try to keep this short and very basic.

I am using three network interfaces (all wired) on the same box.
1. red = public/internet
2. green = local lan (dhcp)
3. orange = dmz (static)

Assume the following simple rules for illustration sake:
1. red input dropped, except releated/established.
2. all green and orange input accepted
3. forwarding turned on so green and orange can flow out red to use the internet.

Assume all is well, and working just fine.


Now here is what I want to do...
I want to write a rule that drops any traffic from the orange network (and orange interface) that attempt to communicate with the green interface, the actual green interface itself.
But here's the thing. I want to accomplish this by using interface names, not IPs.
I know how to do it using IPs, but I do not want to use IP addresses/ranges/networks in any way. And, i'm writing my rules in an iptables-restore script, not a bash script, so no variable substitution.

I tried using iptable's physdev module, but that only seems to work with interfaces that are in a forwarding/bridged relationship.

Does anyone have any ideas?
Thanks!

---

### Post by posterberg on 2015-04-29
Your interfaces should normally get the same name on reboot so you should know which one is eth0, eth1 and eth2
Lets assume eth1 is green and eth2 is orange then issue this to accomlpish what you ask

iptables FORWARD -i eth2 -o eth1 -j DROP

---

### Post by dozy on 2015-04-29
Thanks, posterberg, I appreciate your response, but I have tried that and it only effectively blocks the traffic that wants to pass through the given interface, not traffic targeting the interface itself.

I'll try to be more clear using a new example.

_Example_
I have two interfaces on my firewall: **eth0 **(192.168.0.1) and **eth1 **(192.168.1.1)
I have two machines, one connected to each interface: **Comp0 **(192.168.0.100) and **Comp1 **(192.168.1.100)

Here is what I need:

1. Machines connected to eth0 should not be able to communicate with machines on eth1. Eg. Comp0 cannot talk to Comp1.
    Solved by, ***iptables -A FORWARD -i eth0 -o eth1 -j DROP***

2. Machines connected to eth0 should not be able to communicate with the eth1 interface itself. For example, Comp0 should not be able to ping, ssh, telnet, etc.. into any services on 192.168.1.1.


The only way I know how to accomplish #2 is by specifying the IP address of the eth1 interface in an input rule:
**iptables -A INPUT -i eth0 -d 192.168.1.1 -j DROP**
[B]
[COLOR=#008000]So my clarified question becomes.. Is there a way to block access to an interface by using its name instead of hard-coding its IP address into a rule[/COLOR].[/B]

Something like this (I know this is invalid, I'm just trying to get the point across)
**iptables -A INPUT -i eth0 -d eth1 -j DROP**

(ps. the above will work if I add eth1 to my hosts file as 192.168.1.1, but that's a bad hack I'm sure!)

Thanks again!

---

### Post by posterberg on 2015-04-29
Thank you, you tought me something new today. I was certain that this would be considered to pass the FORWARD chain. I replicated what you said, extremely annoying... ;-)
Your folllow up question beats me, will follow this thread eagerly to see if someone else has a clever solution.

My best alternative suggestion would be this, it would at least cover if you have to change ip address of the interface within the same network range. I know that it isn't what you were hoping for.
iptables -A INPUT -i eth0 -d 192.168.1.0/24 -j DROP

---

