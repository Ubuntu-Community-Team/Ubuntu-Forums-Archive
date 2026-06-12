---
title: "/etc/hosts question"
date: 2005-07-15
forum: General Help
---

### Post by phr4gmonk3y on 2005-07-15
This seems like the most appropriate sub-forum for this question.

Is there a way to make an /etc/hosts entry using a MAC address instead of an ip address?  I use DHCP and every once in a while, I have to reset the router, which changes the internal ip address of the computer I'm adding an /etc/hosts entry to.

Thanks for your help!

---

### Post by ProNoblem on 2005-07-15
I don't know which version DHCPserver you're running, but almost all DHCP servers provide the functionallity to make a list with MAC-adresses and IP-adresses which will always be appointed to a client using the MAC-adres specified.
So the solution is probably in the manuals from your DHCP server.
(Working with the hosts file shouldnt be necesary in this case)

Just remember to use IP-adresses outside your normal DHCP-lease pool, otherwise it could be possible that your DHCP server is giving two pc's the same IP-adres.

---

