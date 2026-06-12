---
title: "Need help with wlan"
date: 2004-10-30
forum: General Help
---

### Post by Marius on 2004-10-30
Hey, 

I have some problems with my wlan nic, dlink dwl-520+ (acx100 chipset). 
Ubuntu has the acx100 module and the firmware it needs, so the card seems to work fine. 

I can't receve an IP from the dhcp-server. I also tried to set up ip manually, but that did't work either. No contact with the router. 
I have windows at the same machine and the network works fine, I get ip from the dhcp-server, no problem at all. 

Some nice helpfull peoples here?

---

### Post by Johan on 2004-10-30
What does your /etc/network/interfaces look like?

---

### Post by Marius on 2004-10-30
Well, I am in windows right now, but i discovered a intresting thing. 
I used "iwlist wlan0 scan" and it just showed a other neighbours network. 
Not the network of the neighbour that share inet with me. Strange, huh? 
So, I dont think the problem is in the interface file.

---

