---
title: "Apache - use same IP address ?"
date: 2012-11-11
forum: General Help
---

### Post by Gordonisnz on 2012-11-11
Hello.

I sometimes turn on my apache server, so I can use wifi & download files etc from my PC to my mobile (android) phone via wifi.

I know that  192.168.xx.xx is a private IP address.

Problem :-  When I restart my PC / Apache server, the IP address changes each time.

IE  

192.168.1.73
192.168.1.76
192.168.1.23
192.168.1.56  etc..

and i have to look it up using IFCONFIG each time.

QUERY:- Is there a way to 'reserve' an IP address for Apache,  and then use the same IP for apache each time it is loaded / activated ?

PS - The server is for my own use - Not for others to access.. (I find it much easier to use this, to xfer files to my android phone.)

---

### Post by lisati on 2012-11-11
As with many things with Ubuntu, there are several possible answers, each with their own merits.

My own preference is to reserve addresses on my local network within my router. The exact way of doing varies between routers.

---

### Post by efflandt on 2012-11-11
If your router does not have a way to assign static IPs by MAC address, just configure your computer with a static IP address instead of automatic.

Most routers are set to just dhcp assign a certain number of IP address less than the network range.  So usually it is safe to pick a high number like 192.168.1.200.  However then you also need to specify netmask (usually 255.255.255.0), gateway (LAN IP of your router) and nameserver(s) (which your router LAN IP also usually handles).

---

