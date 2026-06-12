---
title: "How to change a MAC Address?"
date: 2005-08-01
forum: General Help
---

### Post by geomer on 2005-08-01
Hi people,
I need to change my MAC Address permanently
Where must I put 
ifconfig ethx hw ether 00:00:00...

so that I dont have to do it manually each time I restart my pc?

thanks in advance

---

### Post by adwait on 2005-08-01
If I am not mistaken, the MAC address of any component, is an address embedded into it at the time of manufacturing and cannot be changed.

---

### Post by word_virus on 2005-08-01
[QUOTE=geomer]Hi people,
I need to change my MAC Address permanently
Where must I put 
ifconfig ethx hw ether 00:00:00...

so that I dont have to do it manually each time I restart my pc?

thanks in advance[/QUOTE]

You need to add a line to the file /etc/network/interfaces:

sudo vi /etc/network/interfaces

Find the entry for your ethernet adapter (most likely the block of text that starts with 'auto ethx') and add the line:

hwaddress ether 01:02:03:04:05:06 

at the end of the block. 

Obviously replace '01:02:03:04:05:06' with your new address.

---

### Post by geomer on 2005-08-01
thank you  O:)

---

### Post by word_virus on 2005-08-01
No problem.  Just learned how to do that myself about four hours ago, so happy to be able to pass it along.

---

### Post by Sam on 2005-08-02
[QUOTE=adwait]If I am not mistaken, the MAC address of any component, is an address embedded into it at the time of manufacturing and cannot be changed.[/QUOTE]
Nope, this is a way to do ARP spoofing (using the MAC address of someone else), a cracking method.

IPv6 makes it possible to prevent this.

---

