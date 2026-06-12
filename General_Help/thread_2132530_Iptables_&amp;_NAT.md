---
title: "Iptables &amp; NAT"
date: 2013-04-05
forum: General Help
---

### Post by Drenriza on 2013-04-05
Hey.

I am trying to configure a server with iptables to NAT (with overload, where you NAT multiple local adresses to one public address with port numbers) from a local network(192.168.0.0) to a WAN(83.151.x.x) network.

And been looking at a few guides, but the sytnax for to accomplish this is (to me) complex and easy to misunderstand.
So i'am here for advice.

From what i have found
```

echo 1 > /proc/sys/net/ipv4/ip_forward

```
Enable IPv4 package forwarding.

```

iptables -F

```
Flush all existing rules in all chains.

As i read their is a default nat chain (that dosent show with iptables --list), called nat. Is this correct or have i just misunderstood something?
And does the iptables -F also flush this chain or do u need to execute
```

iptables -t nat -F

```
by itself.

I then found the following two lines for configuring NAT -> [http://pastebin.com/fENBvczx](http://pastebin.com/fENBvczx)
```

# NAT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT


```
Can anyone tell me
[LIST=1]
[*]Whats POSTROUTING does(cant find it in the iptables man or a manual for it). Is it a chain or a option?? 
[*]Whats MASQUERADE? I've tried to find on google what it does, but i dont get a clear answer. 
[*]The above NAT from local to WAN from what i can tell, by saying in the second line Append to FORWARD chain -i (the INSIDE LOCAL interface) ethX -o (the OUTSIDE GLOBAL interface) ethXX -m (unsure what it exactly state after -m does) state --state STATE1,STATE2 -j ACCEPT, would this be correct understood? 
[/LIST]
Hope someone can help me cast some light on this topic.

Thanks on advance.
Kind regards.

---

### Post by Doug S on 2013-04-05
Yes, you need to flush the nat table independent of the others.

Myself, I prefer to use SNAT instead of MASQUERADE. They preform the function of NAT (Network Address Translation) so that packets from somewhere in your 192.168.0.0 network seem to have come from 83.151.X.X.

The state matching module is only ACCEPTing packets that are part of an already existing connection. Typically, this allows reply packets to something you sent out and it is a way to seperate packets you want from others.

POSTROUTING  (and PREROUTING) is a chain, sort of, but not the same sense as the others. Typically, they are only consulted for "NEW" connections where pathways are established for subsquent packet flow through the iptables and connection tracking table. (My description is a little inaccurate, but simplified).

A good reference: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Some other references:
[http://tldp.org/HOWTO/IP-Masquerade-HOWTO/index.html](http://tldp.org/HOWTO/IP-Masquerade-HOWTO/index.html)
[http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html)

Be careful, as there are a great many obsolete "iptables how to"s out there.

---

### Post by Drenriza on 2013-04-12
So i have tried to configure the simple nat rules to allow port NATTING from my local network to the WAN network.
But so far i'am just getting "Destination Host Unreachable.".

What i've done is 


```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

eth0 is my public interface with the 83.x.x.x address.
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```

eth1 is my local interface with the 192.168.x.x address.
```
iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
```

I am trying to figure out to debug the NAT process, but so far i havnt found much on that.
But is it me who is making a obvious mistake or?

---

### Post by Drenriza on 2013-04-12
My bad. It was a network error not a NAT error.

---

### Post by Drenriza on 2013-04-12
I can now NAT from my LAN to the WAN. But if i would like to take my public ip address 83.x.x.x. How can i accomplish the following.

[https://89.x.x.x:80](https://89.x.x.x:80) hits my debian NAT pc which then should redirect me to 172.16.2.10, but ONLY for connections made to 83.x.x.x on port 80.



So far i have 
```
iptables -t nat -A PREROUTING -o eth1 -j MASQUERADE --to-destination 172.16.2.10
```
If the above is correct or incorrect pls let me know. Since i'am far from sure.

And then i need to make a second rule as follows?
```
iptables -A FORWARD -p tcp -i eth0 -o eth1 -d 172.16.2.10 -m multiport --dports 80,433 -m state --state NEW -j ACCEPT
```

Any advice is welcome.

---

### Post by Doug S on 2013-04-12
Now that you have your computer working as a router, you are wanting to add some specific port forwarding. ```
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j DNAT --to 172.16.2.10:80
```
and (which you already have correct):```
iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 80 -d 172.16.2.10 -m state --state NEW -j ACCEPT
```Simiarly for port 443 or via multiport, as you showed.

---

### Post by Drenriza on 2013-04-12
> **Doug S said:**
> Now that you have your computer working as a router, you are wanting to add some specific port forwarding. ```
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j DNAT --to 172.16.2.10:80
```
and (which you already have correct):```
iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 80 -d 172.16.2.10 -m state --state NEW -j ACCEPT
```Simiarly for port 443 or via multiport, as you showed.

Thanks for the reply Doug.

Uhmm not sure if i would call it a "router" ,)

I got a 3 layer Cisco network and are using a Debian server as a firewall / NAT point.

Though, NAT under Debian / Ubuntu could seriously learn something from the way of doing it on Cisco equipment.
Which is much more intuitive and easier to setup / test.

The NAT now works from the WWW to the local LAN. Thanks to your example.
```

iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 80 -j DNAT --to 172.16.2.10:80

```

Can you explain what exactly PREROUTING is and how the DNAT option works.

And is their a difference in 
```

iptables -A FORWARD -p tcp -i eth0 -o eth1 -d 172.16.2.10 -m multiport --dports 80,433 -m state --state NEW -j ACCEPT
```

and
```

iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 80 -d 172.16.2.10 -m state --state NEW -j ACCEPT
```

Or do they accomplish the same thing?

---

### Post by Doug S on 2013-04-15
> **Drenriza said:**
> Can you explain what exactly PREROUTING is and how the DNAT option works.

And is their a difference in 
```

iptables -A FORWARD -p tcp -i eth0 -o eth1 -d 172.16.2.10 -m multiport --dports 80,433 -m state --state NEW -j ACCEPT
```

and
```

iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 80 -d 172.16.2.10 -m state --state NEW -j ACCEPT
```

Or do they accomplish the same thing?Difference: No difference, other than yours does the two ports, 80 and 443 at once. I should not have bothered with that part of my earlier reply, as you had it right already.

The nat PREROUTING chain does any manipulation of a packet before it goes to the routing step, where it will then go to either the INPUT chain or the FORWARD chain. In this case the Destination address is changed to a computer on the internal lan, and thus the routing step will send it to the FORWARD chain. 
There is a handy flow diagram, is addition to other informative content, [here]("http://bodhizazen.net/Tutorials/iptables/").

---

