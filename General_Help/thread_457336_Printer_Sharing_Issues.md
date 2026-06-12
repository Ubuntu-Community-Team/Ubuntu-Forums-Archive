---
title: "Printer Sharing Issues"
date: 2007-05-28
forum: General Help
---

### Post by jasond123 on 2007-05-28
Hey guys. have a bit of an issue and am a complete newbie to linux!!! anyway 

i have a canon mp150 connected to my computer. then my computer connects to a router which then connects to my sisters computer wirelessly. the printer works on my pc but i also need to get it working on my sisters.

i have tried the following.

i selected share printers on my pc. then i went to my sisters and added a printer by selecting network printer. it then asked me for a url so i said ipp://192.168.0.1/printers/multipass-mp150. i then selected the driver and pushed finished but no printer was added. it is just a blank space and an option to add a printer. i also ticked detect network printer before i did the above. i dont now what my computers ip address is so i used the one which i use to access my roter with through mozzilla ie 192.168.0.1. 

Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by AndyCooll on 2007-05-28
The IP address should be that of the box the printer is attached to, not the router. And as a side-point, it might be worth you fixing the IP address for that box too.

You can find the IP address of your computer by typing into the command line the following:
```
ifconfig
```

:cool:

---

### Post by jasond123 on 2007-05-28
Thanks for the fast reply. where can i check my pc ip and what do you mean by fixing it? sorry i am a complete moron!!!

---

### Post by jasond123 on 2007-05-28
cool. i did what you said and a whole lootta stuff came up. can you direct me to what the ip looks like for my pc.

---

### Post by drpaul on 2007-05-28
As the previous poster said

ifconfig

in a terminal window. You are using the command line to find your ip address.

Fixing the ip address means going to your router and assigning it a fixed address, although if your router is like mine it will repeatably use the same address for the same local computer for what seems like forever.

HTH

Paul

---

### Post by AndyCooll on 2007-05-28
See my above post for finding the IP address (I was editing while you were typing).

To fix your IP address it is probably a good idea to look at your router instruction book first. You may want to reserve a few addresses for these purposes (sounds complicated but it isn't really), especially if you have a number of boxes. What I've done is have my router start handing out IP addresses from 192.168.0.20. Then these first twenty I use for static addresses. This way, it means I avoid complications of two boxes picking up the same IP address. 

To fix the IP address in Ubuntu itself, go to System > Administration > Network.

Select your network card then properties. Under configuration select the "Static IP address"
Your three boxes will then probably be something like:
192.158.0.2 (the IP address of your box)
255.255.255.0
192.168.0.1 (the IP address of your router)

:cool:

---

### Post by AndyCooll on 2007-05-28
> **jasond123 said:**
> cool. i did what you said and a whole lootta stuff came up. can you direct me to what the ip looks like for my pc.

It will probably be something like 192.168.0.2 or 3 or whatever.

:cool:

---

### Post by jasond123 on 2007-05-28
ok. i think i found the ip address for the pc. when i used it on my sisters pc the printer did show as ready but when i tried to prnt nothing happened. i am still no sure if i have the right ip coz when i used the ifconfig a hole bunch of info was showing and i used what looked like an ip. still not sure.

it shows 192.168.0.1 my router and then another one which i am not sure if i can post for security reasons. really sorry. i am officialy a moron

---

### Post by AndyCooll on 2007-05-28
> **jasond123 said:**
> it shows 192.168.0.1 my router and then another one which i am not sure if i can post for security reasons. really sorry. i am officialy a moron

Hardly, these are only internal network addresses. Anyway it will be the other other one, and it should be 192.168.0.xx (whatever has been assigned).

:cool:

---

### Post by jasond123 on 2007-05-28
HALELUA i found it. all is right. Tanks alot for ypur help!!!!!!!!!!!!!!:p

---

