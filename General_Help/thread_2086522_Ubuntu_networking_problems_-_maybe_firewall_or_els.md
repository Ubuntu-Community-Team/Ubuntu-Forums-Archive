---
title: "Ubuntu networking problems - maybe firewall or else?"
date: 2012-11-21
forum: General Help
---

### Post by Nikolai D. on 2012-11-21
Hi there,

I am running Ubuntu 12.04 x64 on my Work laptop. I have installed Outlook 2007 with CrossOver. But when i run first config wizard it cant find the exchange server. (It can on Windoz7x64). So i was thinking maybe i can connect with Hamachi to my Home PC running Ubuntu 10.04 x64. But hamachi at work cant login. (On Windoz 7 x64 it does). First i got an explanation from a helpdesker from central administration that it would be related to wrong mailserver config. But now its with hamachi and they havent replied yet to my email with a question if some ports are blocked or not.

So seeing that both Outlook 2007 and Hamachi working and then same things not working on Ubuntu. I wondered couldnt it be that it has to do with Firewall or some other config i need to change?

Thanks in advance,
Nikolai

---

### Post by Nikolai D. on 2012-11-21
i installed firewall configurator and allowed ports: 443, 12975, 32976, 17771. Nothing changes.

---

### Post by reklan on 2012-11-21
are you connecting to the exchange server using the server name or by using its IP address. Try using the IP address as the server name in outlook.

---

### Post by Nikolai D. on 2012-11-21
thank you very much, you are the man! :D

p.s. Now i remember that there were some DNS issues in the network sometimes. How i didnt think of it.

---

