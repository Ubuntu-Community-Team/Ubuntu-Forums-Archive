---
title: "Internet gateway and mutliple interfaces"
date: 2005-10-15
forum: General Help
---

### Post by kake on 2005-10-15
So I was having a problem with having multiple interfaces connected to two different gateways and deciding which one of the interfaces connects to the internet. More detailed I have one wired nic that connects to one gateway and internet. Now when i connect the wireless interface to another gateway it overrides the previous nic (confirmed with netstat -rn) - in effect it now access the internet through the wireless link instead of the wired one, which i would prefer.

I understand this can be 'fixed' manually with route add and del, but this is a combersome way of doings things each time i change location. Is there a way to renew the kernel ip routing table easily. And a way to easily change which eth that should connect to the internet?

I should note that that a part of why i want to know this is because if i disconnect (my wireless connects automatically to a non-secure ap if available, don't know much about how to do a proper disconnect and stay disconnected so i use sudo ifconfig eth0 down) from a wireless gateway and remain connected to the wired one. The wired network will still not connect to the internet if I don't do anything about the route table.

---

### Post by kake on 2005-10-16
For anyone with a problem that are alike mine, seems refreshing the dhclient for the respective eth works fine.

---

