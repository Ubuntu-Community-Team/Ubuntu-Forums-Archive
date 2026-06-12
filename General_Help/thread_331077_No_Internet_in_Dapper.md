---
title: "No Internet in Dapper"
date: 2007-01-04
forum: General Help
---

### Post by titancomputing on 2007-01-04
My network goes.

Cable Modem --> Router --> Computers

One of the computers gets an IP through DHCP no problem. My Dapper box, on the other hand, doesn't. It doesn't have the ability to ping (network unavailable), and trying to use eth0 up and down hasn't been effective. What can I do to get my net working?

---

### Post by bscbrit on 2007-01-04
If its a completely wired network, try this:

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

otherwise, use this:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by titancomputing on 2007-01-04
The first link matches my situation (wired network) but I can't get it to load. All I see is a blank page.

---

### Post by broughcut on 2007-01-04
sorry if this is too obvious but have you enabled the network card in network settings? 

Right click network, properties configure... if not there try System -> Administration -> Networking. (I'm not familiar with Dapper.)

---

### Post by titancomputing on 2007-01-04
Yes, the card shows itself as being enabled.. just not with an IP address. To the guy who posted the link, the link loaded, but it says invalid topic specified.

---

### Post by broughcut on 2007-01-04
if you have DHCP enabled turn it off and try assigning Dapper a static IP in the eth0 configure menu.

---

### Post by titancomputing on 2007-01-04
> **broughcut said:**
> if you have DHCP enabled turn it off and try assigning Dapper a static IP in the eth0 configure menu.

Tried it, no internet.

---

### Post by sargeras on 2007-01-04
I have had this problem on occassion.  For me, running     

sudo route add default gw xxx.xxx.xxx.xxx (ip of your gateway) 

brought the network online.  Hope this works.

---

