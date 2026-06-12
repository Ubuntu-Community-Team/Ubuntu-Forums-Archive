---
title: "2 IP's active at the same time"
date: 2023-12-26
forum: General Help
---

### Post by mudakosarma24 on 2023-12-26
Hi all,

[COLOR=#1A1A1A][FONT=&quot]I'm tasked with assigning an additional public IP address for temporary remote access[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]but seems as only single interface can stay active, not both at the same time[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]this is original assignment (for some reason it's DHCP, but don't wanna mess with it ) 
[https://i.imgur.com/P2CeOeS.jpeg](https://i.imgur.com/P2CeOeS.jpeg)[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]so they added an additional interface, where I simply configured public IP info that was provided[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot][https://imgur.com/FV7feFs](https://imgur.com/FV7feFs)[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]so now, only way that public IP works is if I take first interface down (so configuration is good) .. but that beats the purpose of temp remote access
if I bring both interfaces, only single stays active[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]I need to have both interfaces up at the same time[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]what is it that I'm doing wrong?[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-12-26
You can have 5 addresses assigned to one standard NIC (even without SR-IOV)... Search on logical "multi-homed addressing" or "IP Aliasing"...

---

### Post by mudakosarma24 on 2023-12-26
hmmm I'm not sure if that will work

public IP is on a different network, that interface one can't reach 

it needs to be on a separate NIC that has cable plugged in

---

### Post by MAFoElffen on 2023-12-26
<<This thread should probably be better suited to the "Networking" Section>>
Correct. Your ISP would have to be in on it. Your point of entry with your ISP is probably singular... Right? 

What you describe on adding another NIC is not true either in that respect. Why? --> Becaseu the about is not going to change without something config'ed with your ISP whether you have one or 20 physical NIC's unless that is what you pay for from your ISP... Or you 'are' the ISP. Either way, config is going to be needed on both sides of that connection to make that work.

Being I do networking beyond just "Local", that is still true... You can divide up a physical NIC with unlimited addresses (until you effectively run out of addressable addresses)... The way you can do that is to subnet the address, then alias it with different ip addresses.
RE: 
[https://www.cisco.com/en/US/docs/ios/11_0/access/configuration/guide/acip.html#wp1308](https://www.cisco.com/en/US/docs/ios/11_0/access/configuration/guide/acip.html#wp1308)
[https://www.geeksforgeeks.org/alias-secondary-ip-address/](https://www.geeksforgeeks.org/alias-secondary-ip-address/)
[https://superuser.com/questions/1184980/network-interface-and-ip-aliasing](https://superuser.com/questions/1184980/network-interface-and-ip-aliasing)
[https://docs.oracle.com/cd/E13209_01/wlcp/wlss40/confignetwork/network_arch.html](https://docs.oracle.com/cd/E13209_01/wlcp/wlss40/confignetwork/network_arch.html)

What does take multiple NIC's, when I setup for more bandwidth, is to do the opposite of that. Bonding multiple ways in as a single path...
RE:
[https://www.cisco.com/c/en/us/td/docs/ios/12_2sb/feature/guide/gigeth.html](https://www.cisco.com/c/en/us/td/docs/ios/12_2sb/feature/guide/gigeth.html)
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)
[https://www.server-world.info/en/note?os=Ubuntu_22.04&p=bonding](https://www.server-world.info/en/note?os=Ubuntu_22.04&p=bonding)

Is this real-world for work (production), your own education, or a class assignment?

---

### Post by SeijiSensei on 2023-12-26
> **MAFoElffen said:**
> Correct. Your ISP would have to be in on it. Your point of entry with your ISP is probably singular... Right? 

In the past I've managed to get an IP subnet assigned by my ISP in commercial settings. Then you can use aliasing to assign separate IPs in the subnet to different virtual adapters, e.g., assign eth0:0 to 192.168.0.1, eth0:1 to 192.168.0.2, etc. 

That's harder to find these days as the public IP space grows more limited. But you'd only need a /30 or /31 to handle just a couple of addresses. I once had an ISP grant me an entire /27, or 30 assignable addresses! My guess is those days are long gone.

---

### Post by mudakosarma24 on 2023-12-26
I bit off more than I can chew

in my head this was simple as assigning static IP to an interface, guess it's not

ohh well, tomorrow is a new day and and I'll try teach my self how to do this

thanks everyone for response
edit: 
any youtube tutorials (or close enough) for what I'm trying to achieve?

---

### Post by MAFoElffen on 2023-12-26
Easier than you think, if you have a say i both sides of the equation...

See the attached screenshot from on of my server VM Guests.

That is 5 Ip's on the same NIC in the same NetID... (not on different subnets)

You can still creative. It's just that you need some guidance and control on both sides. Both of those are... In an internal local network.

---

