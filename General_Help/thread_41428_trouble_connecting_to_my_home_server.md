---
title: "trouble connecting to my home server"
date: 2005-06-13
forum: General Help
---

### Post by talz13 on 2005-06-13
All the other computers on my network have no problem addressing my home server by its local address (server, or 192.168.1.5, either one).  My laptop on ubuntu just can't seem to do it.  I can only see the server if I go through my web address.  

Also, I can't connect to my router either.  I just get timeout errors when going to the IP.  There must be something wrong in my configuration somewhere.

What could cause my wireless connection to be unable to connect to my local network resources?

---

### Post by GrammatonCleric on 2005-06-13
What is you network config of your box (i.e. ip, mask, gateway).  Is your box firewalled with a local firewall (i.e. firestarter)?  When connecting to your house server what OS is it running?

- G

---

### Post by talz13 on 2005-06-13
[QUOTE=GrammatonCleric]What is you network config of your box (i.e. ip, mask, gateway).  Is your box firewalled with a local firewall (i.e. firestarter)?  When connecting to your house server what OS is it running?

- G[/QUOTE]

This machine shouldn't be firewalled, never configured one, and don't see any firewalls running.

The ip, subnet, gateway are all setup the same as the others, 192.168.1.x, 255.255.255.0, 192.168.1.1

The server's running FC3 and has no trouble interacting with the other machines on the network.  I can still access it if I go through my ISP ip address to a forwarded port (i'm doing that right now for webmin from school from my laptop), but even a simple ping to any of the computers on my network fails.

I'll check my subnet again when i get home, but I believe it should be correct.

---

