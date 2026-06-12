---
title: "DHCP/Cable modem dilemma"
date: 2005-06-18
forum: General Help
---

### Post by thewhatsit on 2005-06-18
Hey,

I just switched ISPs from roadrunner to Adelphia. I am running Hoary and internet worked fine with roadrunner. Now I'm having problems, but its clearly not a problem with my nic.  

I'm using a dell laptop, and I have two hardrives that I swap between. One runs windows and the other linux. The windows works fine using DHCP. 

On linux when I boot it pauses at configuring network interfaces for a long while. Eventually gives the Ok and then moves on. However, when i get to the command line, and issue an ifconfig eth0 I don't have an ip address. 

I thought it might be a dhcp problem and read that some people use dhcpcd so I unintstalled dhclient and installed dhcpcd and got no change. The nameservers appear to be correct in /etc/resolv.conf as well as the search domain. Also, when i first boot and don't have an ip there is nothing in the routing tables.

I'm not using a router so I'm connected directly to the cable modem. On windows I can acces the cable modem from 192.168.100.1 in the browser.  Since I'm connected directly to the modem should my ip be in the 192.168.xx.xx range or an internet ip? I tried using a static ip addres on linux with the ip my windows box obtains with no luck.  Is there some way to check my DCHP settings and possibly find out whats wrong.? Please let me know. Thanks

---

### Post by bosshoff on 2005-06-18
I had some trouble with Adelphia at first;  however, I think my issue was unrelated.  However, just in case, I'll tell you what happened:

The cable modem was holding onto the MAC address of a box I had it plugged into, and when I switched boxes, ergo NICs, the modem went "dur, what's this, davey?" and  proceeded to do nothing at all.  To fix this problem, I turned off my modem for about five minutes between switches.  Of course, now I've wised up and am using a home brewed linux router (don't even ask me to explain iptables...what an exercise in obfuscation that configuration is...).  

As for your other question concerning the 192... IP, that is definetely not what it should have if your modem isn't also some NAT box too.  The fact that you can actually access its config from a browser lends me to believe it is more than a simple cable modem.  The cable modem I have has no such ability, so it may just mean that mine is cheaper (in fact, it was the cheapest one I could find  ;-) )

Give us the model number on that shizzle, so we can be better informed.

Hope this helps.

---

### Post by bosshoff on 2005-06-19
Alright, so my Adelphia connection failed last night, and I was fooling around with the modem, and I can in fact get to a web config.  I have no idea what it is for, other than confirming what my LEDs tell me.

---

