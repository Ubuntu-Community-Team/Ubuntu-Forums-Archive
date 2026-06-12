---
title: "Networking"
date: 2008-06-24
forum: General Help
---

### Post by Black Mage on 2008-06-24
Hey,

I'm trying to network my house and I bought a layer 2 switch, a Netgear GS716T Switch to be exact. And I just realized it doesn't give out DHCP nor can I route the incoming IPS.

So on this switch, do I have to install a DHCP server in order to give IPS and a firewall in order to route incoming traffic correctly?

Thanks in advance for any advice/help.

---

### Post by danwood76 on 2008-06-24
You need a router to connect your LAN to the Internet.

If you are just setting up a home LAN you dont need DHCP, you can set IP addresses manually.
You need to make all of your PC's have the same subnet mask (Usually 255.255.255.0) and all within the same IP network (Home LANs are usually 192.168.0.x)

So for example:
PC1 = 192.168.0.1
PC2 = 192.168.0.2
PC3 = 192.168.0.3
etc.

---

### Post by timcredible on 2008-06-24
like the other poster said, replace your switch with a switch/router that will do dhcp and nat and firewall.  they're probably about $100US for one with 4 or 8 ports.  when i signed up for verizon dsl, they sent me a westell 327w to connect to their line, it has 4 ethernet ports, wireless, does dhcp, firewall, port forwarding, nat, all the usual stuff.  maybe check with your isp and see if they'll give you something (assuming you're on broadband).

---

### Post by msgmikeh on 2008-06-24
Right, a router is needed. A switch will expand the number of ports you have available. Basicly, a switch is a smart hub. As in a hub will share the bandwidth to all ports, and a switch will share bandwidth for only the ports that are communicating.

Of course, this is in basic terms. 

Mike

---

### Post by Black Mage on 2008-06-24
Ok thanks. Can I use the router and the switch at the same time? Because the switch I have has gigaports on I want to keep making use of that especially since I'm streaming video from computer to computer. So basically if I get a router, which doesn't need to be that fast since my fastest internet connection is only 5 Mbps, can that router do port forwarding to a computer on the switch with a certain ip?

And its a $200 dollar switch I can't return so i want to make the best use of it :).

Would something like this do the trick?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122007](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122007)

---

### Post by danwood76 on 2008-06-24
Yes the switch will just extend the amount of ports you can use.
Connect all your gigabit LAN on your switch and just one connection from the router to the switch will do you.

---

### Post by Gunman1982 on 2008-06-24
> Ok thanks. Can I use the router and the switch at the same time?
Yes, just plug the router into the switch. If the router has an integrated switch (more than 1 port for lan) than connect one cable from the router to the uplink port of the switch. Or get a crosslink cable.

> So basically if I get a router, which doesn't need to be that fast since my fastest internet connection is only 5 Mbps, can that router do port forwarding to a computer on the switch with a certain ip? 
Most of the routers nowadays provide such a function, but many are restricted on the amount of rules.

---

### Post by danwood76 on 2008-06-24
> **Gunman1982 said:**
> Yes, just plug the router into the switch. If the router has an integrated switch (more than 1 port for lan) than connect one cable from the router to the uplink port of the switch. Or get a crosslink cable.

This isnt necessary any more, most switches these days are auto negotiating in speed aswell as data direction.
I bought a really cheap router the other week and it automatically set the data direction without a crossover cable to my really old switch.

Port forwarding is always to specific IP's, and it will forward round the switch perfectly.
This is what happens within the router anyway with the 4 port switch that is attatched to it.

---

### Post by Black Mage on 2008-06-24
> **danwood76 said:**
> This isnt necessary any more, most switches these days are auto negotiating in speed aswell as data direction.
I bought a really cheap router the other week and it automatically set the data direction without a crossover cable to my really old switch.

Port forwarding is always to specific IP's, and it will forward round the switch perfectly.
This is what happens within the router anyway with the 4 port switch that is attatched to it.
out
Ok, so from router to my switch, I need a cross-over-cable also.

---

### Post by danwood76 on 2008-06-24
No just a straight standard Cat5e (ethernet) cable will be fine.
Gunman1982 was saying some out of date info.

Switches and routers used to need crossover cables between them but as technology has advanced this has become redundant.

---

### Post by Black Mage on 2008-06-24
Ok, thanks guys. That helps a lot.

---

### Post by Black Mage on 2008-06-24
Any good router suggestions for this?

---

### Post by danwood76 on 2008-06-24
What type of internet connection do you have?

Most routers will be fine but if you are doing a lot of bit torrent stay away from netgear.
Thats speaking from personal experiance as their routers used to crash after making 100 connections or something similar.
I always recommend buffalo routers as they seem very stable.

---

### Post by Black Mage on 2008-06-24
> **danwood76 said:**
> What type of internet connection do you have?

Most routers will be fine but if you are doing a lot of bit torrent stay away from netgear.
Thats speaking from personal experiance as their routers used to crash after making 100 connections or something similar.
I always recommend buffalo routers as they seem very stable.


I have cable but I'm going to be switching to DSL soon for a cheaper static IP, so either way the fastest I will have is a 6 Mbps connection. And besides having port forwarding to a webserver, I'm going to need port forward to a database server. My current router does port forwarding but is unusually slow when connecting to a db.

---

### Post by Black Mage on 2008-06-24
Ok, so I decided to go with this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833122081](http://www.newegg.com/Product/Product.aspx?Item=N82E16833122081)

---

