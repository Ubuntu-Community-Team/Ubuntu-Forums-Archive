---
title: "Open iptables port to incoming port from a dynamic IP Address"
date: 2015-09-22
forum: General Help
---

### Post by Ian_Chilvers on 2015-09-22
Hi

Ok, here's the scenario.

You have an Ubuntu Server on a dedicate root server on the Internet somewhere with a public IP address, at the backend home office you have a small LAN connected to the Internet using a DrayTek Vigor Router.
The ISP __ONLY__ provides dynamic IPs and switching ISP for static IPs isn't possible.

You want to use iptables on the Ubuntu server to lock things down but open up SSH to the home network, but how would you do this with a dynamic IP Address?

Options? Discuss??

---

### Post by SeijiSensei on 2015-09-22
Do the DHCP-supplied addresses all fall into a specific IP subnet? You could permit the subnet to connect via SSH. That would be vulnerable to a rogue host in that subnet, but you still have the usual authentication peocesses as well. Shared keys and no root logins are effective there.

---

### Post by Ian_Chilvers on 2015-09-23
Hi.  They are on the same subnet but its a large public range of addresses.

Any other ideas??

---

### Post by SeijiSensei on 2015-09-23
I'm not talking about the ISP's entire network.  Usually most large ISPs have local subnets and local DHCP servers.  It's quite possible your addresses come from a pool of just a couple thousand or even fewer.

How often does your address change?  I've had the same address from my ISP, Verizon FiOS, for months now.  Have you identified any pattern in the addresses you get?  Are the first two "octets" (e.g., 192.168 in 192.168.1.0/24) always the same?  How about the third?

---

