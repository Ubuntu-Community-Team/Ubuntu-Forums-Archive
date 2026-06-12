---
title: "internet securiy"
date: 2007-03-07
forum: General Help
---

### Post by joriad on 2007-03-07
For a while now I have noticed my activity light on my cable modem was in a constant state of activity even though I did not have any web browser opened or any other program (that I am aware of) that needed to have constant access to the Internet. When I first subscribed to broadband Internet I was using only windows xp and do not recall this light being in a state of constant activity. Now that I am using Ubuntu 6.10 exclusively I have noticed this activity. Could this Internet activity simply be Linux checking for updates, my modem keeping in touch with my isp or network card, or could this indicate a vulnerability? The usual activity I have noticed is send usually less that 1 kb/s and receive usually less than 5 kb/s, however at times I have noticed larger chunks of data being sent and received. Is their a way I can check who is requesting this data and what data is being sent and received?

---

### Post by wieman01 on 2007-03-07
> **joriad said:**
> For a while now I have noticed my activity light on my cable modem was in a constant state of activity even though I did not have any web browser opened or any other program (that I am aware of) that needed to have constant access to the Internet. When I first subscribed to broadband Internet I was using only windows xp and do not recall this light being in a state of constant activity. Now that I am using Ubuntu 6.10 exclusively I have noticed this activity. Could this Internet activity simply be Linux checking for updates, my modem keeping in touch with my isp or network card, or could this indicate a vulnerability? The usual activity I have noticed is send usually less that 1 kb/s and receive usually less than 5 kb/s, however at times I have noticed larger chunks of data being sent and received. Is their a way I can check who is requesting this data and what data is being sent and received?
I would check the router (through HTTP?) and see what MAC address/IP addresses appears in the log-files. Also watch your router while your computer is turned off. Have you got a wireless access point enabled?

---

### Post by joriad on 2007-03-07
I don't have a router,  unless when you refer to router you mean my cable modem. however when my computer is off so is the activity light. My isp (charter communications) uses  DHCP so I don't know what I would be looking for as an Internet address and I don't know how to check for a MAC address of the modem. I found 2 DNS addresses and a local host address but nothing else. I also don't have a wireless connection so wireless access points are non existent. I will look for MAC address info tonight to see if I can see what they are. If you have information on how to check let me know. Thanks for your help

---

### Post by Mr. C. on 2007-03-07
What traffic appears on your network depends upon what services you have running.

A fair amount of traffic is normal, and you certainly can't control outsiders sending traffic your way.

There are various ways to monitor what traffic is going out over, or into, your network.  Most consumer routers have minimal logging, and the freebie appliances given to your by your provider certainly won't have much.

If you want to monitor traffic, either configure your system with iptables, and log all traffic, or use tcpdump or other tools to monitor traffic (this isn't trivial for the inexperienced).

You should have a firewall (aka: network appliance, router) between your systems and your broadband modem.  Your system is wide open to attack otherwise; and attacks are constant (eg. hundreds to thousands per day).

MrC

---

