---
title: "How to use Ubuntu Server to display messages in web browser automatically"
date: 2013-09-29
forum: General Help
---

### Post by coss-cat on 2013-09-29
Hello Everyone,

I would like to do the following (searched the internet before posting here with no success though):

Premises:
- i live in a small block of flats and i have a thinkpad X61 laptop that runs Ubuntu server 12.04 LTS 
- I have a fiber optic net connection that allows me to share some of my net to my 3 neighbours (already did it :))
- unfortunatelly because of a design matter, I am the one that holds all block's comune facilities (water pump runs from 
my electric current; outdoor lights as well etc.) so i am the self procalimed "administrator" (which i hate a lot !!!)


Solutions that I seek forward:

- given the upwards facts I need to do something that displays each time my neighbours open a browser a message
that they need to pay an amount of money for the past month replacing my "admin" atributes. I can do the logic to
calculate the montly fees, but don't know how to do the thing with displaying stuff in browser. I saw this to some 
internet providers that anounce you with few days before how much you have to pay for a given month.
- I need to do something also to control dinamically the throughput that gets to each of my neighbours; meaning that when
only one is connected he will get full speed of internet, when someone gets connected too, the first one will be limited and 
the band will split to 2 etc.

I am ready to modify everything including buying an aditional lan card (insert in PCMCIA) and transform the Ubuntu server 
into a router etc. 

Small description of the network I have:
Fiber gets into my house where there is a Media Converter (MC) that converts to wire (RJ45); From here I plugged this wire into
a wireless router (D-Link DI-524; very old ... will be changed soon with an other one). From here, each of my neighbours get a 
UTP cable into their house, where a wireless router is installed. Resume: From my router that gets signal through WAN port I
send through 3 wires from LAN ports signal to 3 WANs of 3 different routers



Hopefully you got the idea. 

Thank you all for suggestions and have a nice day.

cosscat

---

### Post by JKyleOKC on 2013-09-29
> **coss-cat said:**
> - I need to do something also to control dinamically the throughput that gets to each of my neighbours; meaning that when only one is connected he will get full speed of internet, when someone gets connected too, the first one will be limited and the band will split to 2 etc.I can't help with the primary question, but this one is easier. You don't have to do anything to make this happen; it's automagically done at the other end of the fiber. The line's bandwidth (throughput) is limited. If one machine is usinhg it, it will get the full amount. If two are on line, each will take what they need but the total will never go over the limit and it will average out to each getting half.

However if you want to force an even split, that's a different matter, and will probably require more advanced equipment than a standard home router. You might ask over in the Networking area, where you'll find the experts in the subject...

---

### Post by coss-cat on 2013-09-30
Thank you [**[COLOR=#000000]JKyleOKC[/COLOR]**]("http://ubuntuforums.org/member.php?u=374258")[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=374258")[  						 					]("http://ubuntuforums.org/member.php?u=374258")

---

