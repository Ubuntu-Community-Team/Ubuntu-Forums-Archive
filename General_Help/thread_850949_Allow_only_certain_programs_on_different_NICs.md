---
title: "Allow only certain programs on different NICs"
date: 2008-07-06
forum: General Help
---

### Post by iloveannie on 2008-07-06
Is it possible to let only certain services operate on different network interface cards?  Ideally, I would like my setup as follows- 

Internet <------> apache box <------> database box

I want the apache box to have two NIC cards:
One connected to internet for serving dynamic web pages
The other connected to a database box. 

The reason I want this setup is that then I don't need to secure the database box since nobody can directly connect to it.

:-k

Can this be secure, or is this a bad idea?

---

### Post by danwood76 on 2008-07-06
It is possible, I think you can probably just setup 2 networks.
One with your internet and one with your database.

Simply sticking the database server in a different IP network and possibly subnet mask will stop it from being able to ba accessed by the internet whilst still being accessed by your apache server

Many Unix Servers do the exact thing you speak of, plus there are many types of firewalls and routers that are used for the very purpose of splitting internet (apache servers) and internal networks whilst still allowing internet access.

---

### Post by iloveannie on 2008-07-06
How do I do that?

---

### Post by danwood76 on 2008-07-06
Well ok lets say that NIC1 is connected to your router (Internet network) and NIC2 is connected to your database server.

NIC1 will probably get its IP from the router through DHCP, this IP will always be within a specific IP range. For example 192.168.0.xxx

This network connection you can leave to set itself up theough DHCP, the next thing you do is decide on an IP range for your second network (with the database on).
It needs to be a different IP network than NIC1, so you set them to both use static IPS in the same range.
So a different IP net would be 192.168.1.xxx, so set your NIC2 to be 192.168.1.1 and your database to be 192.168.1.2.
Connect the two PCs through a switch or a crossover cable and they should then be able to talk to each other.

To be honest you will get better speed results if the database is on your main apache server, the other thing is that you will need to open the database up to have the same access as if it were on the same PC anyway so I doubt that there is much of a security benifit to doing this over just using a good firewall on the first PC.

---

