---
title: "Internet through PPPoE on Ubuntu"
date: 2007-04-09
forum: General Help
---

### Post by warlock_handler on 2007-04-09
Hi guys 
I need to connect to my internet its a adsl connection with authentication... basically a connection through PPPoE and i have username and password for it...

can someone tell me how do i connect to it in Ubuntu also how do I setup my router so that i can share my internet...

please help

ps i have tried this [[www.roaringpenguin.com/pppoe/]](www.roaringpenguin.com/pppoe/]) but it keeps giving me this error
"Link is down -- could not find interface corresponding to pppd pid 2934"

---

### Post by m.musashi on 2007-04-09
Hmmm. This shouldn't be a problem. I used to use DSL and PPPoE with authentication. Nearly all of the set up was done in the modem including the authentication part. The only set up on Ubuntu was to open networking and activate the right device (for me it was eth0) and set it to DHCP. If you are using a static IP you can set that too.

If you are going through a router then it's pretty much the same as far as Ubuntu is concerned.

Can you be a bit more specific to what you need help with? Trying to explain the whole process will be a bit complicated.

EDIT: I don't think you will need the roaring penguin client if you have a router. I can't speak to its need without a router as I don't have that experience. I used a router and the DSL.

---

### Post by warlock_handler on 2007-04-09
> **m.musashi said:**
> Hmmm. This shouldn't be a problem. I used to use DSL and PPPoE with authentication. Nearly all of the set up was done in the modem including the authentication part. The only set up on Ubuntu was to open networking and activate the right device (for me it was eth0) and set it to DHCP. If you are using a static IP you can set that too.

If you are going through a router then it's pretty much the same as far as Ubuntu is concerned.

Can you be a bit more specific to what you need help with? Trying to explain the whole process will be a bit complicated.

EDIT: I don't think you will need the roaring penguin client if you have a router. I can't speak to its need without a router as I don't have that experience. I used a router and the DSL.

ok sir, 
i have i guess the same dsl and ppoe connection with authentication, now i setup my network settings (system> Administration> Networking) so that my eth0 gets everything from the DHCP...

Now can u explain this part of your statement
"Nearly all of the set up was done in the modem including the authentication part."

i plugged my net cable to my router.. and from the router i got a cable to my LAN card... I have my user name and password... now can someone please explain me how do i go about this thingy... i cant understand... what to do next.. and how to connect...

ps i have my server IP and my own IP...  (i had chked it from my winXP laptop.. pluged my net cable there.. and connected over PPPoE and chked my server IP and my own IP.)

---

### Post by m.musashi on 2007-04-09
> **warlock_handler said:**
> Now can u explain this part of your statement
"Nearly all of the set up was done in the modem including the authentication part."

Yes. I my case I had to open the dsl modem configuration page which is built into the modem. I accessed it using a web browser. You might need a manual to know the correct IP address of the modem (assuming yours has that option) but for me it was 192.168.1.100. Once in the set up utility I can set up the PPPoE authentication and other parameters.

Before you can do this, you will probably need to access the router's set up utility and point it at the modem (or use DHCP). I have a Linksys router and the set up IP for that is 192.168.1.1. I can't speak for certain about your hardware. Anyway, once you have the router getting an IP from the modem and the modem getting an IP from the ISP (and properly authenticating) you should be good to go. Reboot or restart networking and in a perfect world you'll be good to go.
```
sudo /etc/init.d/networking restart (that's from memory and I'm at work so if it's wrong I apologize)
```

Just a thought, when you say authentication do you mean for your ISP or something else?

Sorry this is rather generic but I don't have a clear understanding of your situation yet. If none of this helps please post back with info on the steps you have taken and where you are getting hung up and I or someone else will be more than happy to help.

---

### Post by zvacet on 2007-04-09
After choosing dhcp is your type of connection and have gateway address>close.In DNS tab put your nameserver address instead one you find there when you open DNS tab.Close.
```
pppoeconf
```

---

### Post by warlock_handler on 2007-04-10
> **m.musashi said:**
> Yes. I my case I had to open the dsl modem configuration page which is built into the modem. I accessed it using a web browser. You might need a manual to know the correct IP address of the modem (assuming yours has that option) but for me it was 192.168.1.100. Once in the set up utility I can set up the PPPoE authentication and other parameters.

Before you can do this, you will probably need to access the router's set up utility and point it at the modem (or use DHCP). I have a Linksys router and the set up IP for that is 192.168.1.1. I can't speak for certain about your hardware. Anyway, once you have the router getting an IP from the modem and the modem getting an IP from the ISP (and properly authenticating) you should be good to go. Reboot or restart networking and in a perfect world you'll be good to go.
```
sudo /etc/init.d/networking restart (that's from memory and I'm at work so if it's wrong I apologize)
```

Just a thought, when you say authentication do you mean for your ISP or something else?

Sorry this is rather generic but I don't have a clear understanding of your situation yet. If none of this helps please post back with info on the steps you have taken and where you are getting hung up and I or someone else will be more than happy to help.

Dude thnx for you help.. but a dumb thing i realized.. my Linksys router allows to connect over PPPoE so i if i plug my connection to the router and connect from there it works fine..  but now the very stupid fuckup is that my ISP allows only singer user access.. so its logged my laptops MAC address.. and now i cant connect from anywhere else..  i tried cloning my MAC address on my router.. but its still not leting my connect through my router...

---

### Post by m.musashi on 2007-04-10
My suggestion would be let the modem hand out one IP to the router and then let the router hand out as many IPs as you need. As far the ISP is concerned you will only have one computer connected (the router). That would be the easiest but you would have to get your modem and router talking. It's not too difficult though. If you are locked to a single MAC address now, you might need to contact the ISP and have them release something so you can get the modem-router set up. If they are not in favor of you using a router don't volunteer that info. Just tell them you goofed up and want to start over.

---

### Post by warlock_handler on 2007-04-10
> **m.musashi said:**
> My suggestion would be let the modem hand out one IP to the router and then let the router hand out as many IPs as you need. As far the ISP is concerned you will only have one computer connected (the router). That would be the easiest but you would have to get your modem and router talking. It's not too difficult though. If you are locked to a single MAC address now, you might need to contact the ISP and have them release something so you can get the modem-router set up. If they are not in favor of you using a router don't volunteer that info. Just tell them you goofed up and want to start over.

haha.... good suggestion... will try it out...

---

