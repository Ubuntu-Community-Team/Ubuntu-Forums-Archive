---
title: "is this possible with Ubuntu? Please help."
date: 2008-02-28
forum: General Help
---

### Post by boeing777 on 2008-02-28
Hi guys, I'm trying to install Ubuntu on my old computer to act as a router for my home network of 7 computers. My old computer is running athlon processor at 1.7Ghz.

We are currently using a TPLink wireless router to share internet connections among 7 computers in our house, unfortunately, two of them are always downloading movies and it's really slowing down the network/internet and my TPLink Router does not support any bandwidth management. Here is what I'm trying to do:

Set up my old computer installed with Ubuntu as a router. Then connect my current TPLink router to the Ubuntu router and then connect the Ubuntu router to the cable modem. So all of the network traffic will be going through two routers: 1. TPLink Wireless Router ----> 2. Ubuntu PC Router ---> Cable Modem.

I was just wondering is it possible for this kind of configuration(passing through two routers) and trying to control the bandwidth for each computer with the Ubuntu router.

---

### Post by boeing777 on 2008-02-28
up

---

### Post by Scunizi on 2008-02-28
It is possible but your TPlink router must have a function that allows it to become a switch.  That is, it can't provide dhcp and must be just a pass through device.. As for how to configure Ubuntu to be the actual router is beyond my expertise.. I just know it's possible.. You might ask on IRC.freenode.net /join #ubuntu using an IRC client like xChat.

---

### Post by boeing777 on 2008-02-28
My router has something called static switching which allows me to redirect traffic to another gateway

---

### Post by Whiffle on 2008-02-28
Is it possible to put dd-wrt or another firmware on that router?  Then you could do it all on the router.

---

### Post by Scunizi on 2008-02-28
I have a linksys (uses linux,, could put DD-wrt on it but haven't).  My router under setup/advanced routing allows me to choose "Gateway" or "Router".  Gateway can act as a DHCP server or Static server, Router allows just a basic passthrough.

---

### Post by boeing777 on 2008-02-28
do you know any firmware for Linksys that supports speed limit?  like setting max upload/download speed for individual clients connected to the router?  If it can, then I would just spend some money on a Linksys router instead of using my old computer as a router.

---

### Post by Scunizi on 2008-02-28
Since I haven't played with other firmware I really couldn't say.  However, here's the link for [DD-WRT]("http://www.dd-wrt.com/dd-wrtv3/index.php").  You'll probably find your answer there.

---

