---
title: "Phone able to connect to the server but computers unable to"
date: 2014-09-29
forum: General Help
---

### Post by Daniel_Wong on 2014-09-29
Hi there,

I am having difficulty connecting to services on my lubuntu computer from outside my LAN network. I am running a utorrent server and a LAMP server on the computer. I have the computer automatically updating a dynamic DNS name using duckdns.

When I try to connect to say the utorrent server using the duckdns address ([http://mydomainname.duckdns.org:8080/gui/](http://mydomainname.duckdns.org:8080/gui/)) from a computer, the connection fails. However when using the lan IP address it accesses it correctly (192.168.0.5:8080/gui/). Also, when just using the duckdns address without portnumbers and such it will go to the router setup page.

I believe I have port forwarded correctly as when accessing the utorrent server from my phone or tablet, it will connect successfully using the duckdns address. This is the same when using just the duckdns address without the port numbers and such, I am able to access the LAMP servers index.html page without being directed to the router setup page.

This problem makes no sense to me as computers are unable to access the services but mobile or tablet devices are. Is this due to mobile web requests being handled differently to computer requests?

Any help would be greatly appreciated :) Thanks.

[EDIT 30/09/2014] 
I managed to solve it, apparently my router doesn't have something called NAT loopback so all my attempts from within the network does not work. Testing the access from outside the LAN network shows that I had it all configured correctly :3

---

### Post by John_Ten on 2014-09-30
You are trying to access a computer behind a router, you can't do that, that's why you get the router setup page. What you can do is set up port forwarding on your router, so when an outside computer tries to connect to port 8080, it will redirect it to 192.168.0.5 port 8080. For more on that see your router's manual. Make sure your phone and tablet are using the same internet connection as your computer when you do the tests, I don't think the router can distinguish between the two. Also, check if your computer is not to blame, maybe you have set up some proxy or firewall there, also check it in another browser.

---

