---
title: "Internet help"
date: 2007-07-06
forum: General Help
---

### Post by helliewm on 2007-07-06
See screenshot of my Routers webpage:

All 3 of my computers appear connecting to the internet. However the computer lablled/named helen-raffles has the green status bar to say its connected to the internet yet I cannot open any web pages anyone any ideas? 

I have doubled the checked the WEP password and tried just an open connection with no encrption but it makes no difference-it is a wireless connection.

I am really stuck??

Helen

---

### Post by eggdeng on 2007-07-06
Are you able to ping any IP addresses outside your LAN? Might be an idea to move this thread to Networking & Wireless.

---

### Post by helliewm on 2007-07-06
No its pinging any other Ip's

Helen

---

### Post by smiley2billion on 2007-07-06
I agree with eggdeng,

Open up a terminal and type:

ping 64.233.169.99

This is googles IP address.  If you start getting something that looks like this:

64 bytes from yo-in-f99.google.com (64.233.169.99): icmp_seq=20 ttl=240 time=54.1 ms

Then you've got a working internet connection but your DNS server settings would seem to be wrong.  If you do get a response like the one above (you'll get several) try putting the 64.233.169.99 in a web browser instead of [www.google.com](www.google.com) and see if it brings up the page.

If none of that is working try unplugging your router for 30 seconds or so and plug it back in.  Sometimes routers go all goofy and do not properly pass traffic.

---

### Post by eggdeng on 2007-07-06
> No its pinging any other Ip's I suppose you mean it's not pinging any other IPs. Can you ping the router?
There lots of tips at at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

