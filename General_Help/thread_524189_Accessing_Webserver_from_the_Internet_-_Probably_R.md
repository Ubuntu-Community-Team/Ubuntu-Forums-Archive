---
title: "Accessing Webserver from the Internet - Probably Router/ISP Help"
date: 2007-08-12
forum: General Help
---

### Post by Frostbain on 2007-08-12
Hey hey,
I know similar questions have been asked; and I tried their solutions, but they didn't work.


Problem:

Set up a web server, using Webmin; and added an Apache server using various forwarded ports (80, 8080, and even a random 6883).  I can access 80 and 8080 from anywhere within my network (all computers on the network are behind a router;  the web server, my personal computer, and my laptop are also behind a switch that's behind the router); however, I cannot access any of them from outside my network (i.e. the internet) using the IP address and the port number.
The other suggestions I've read are that the router generally blocks requests like that  from within the network, so it was suggested to have a friend try it.  I did, to no avail.




The current set up:

-Router (LinkSys WRT54G, firmware 1.00.9) forwards ports for the web server (22, 80, 5900, 10000, and 8080) to the servers LAN IP address.  The web server, my personal computer, and my laptop are behind a switch which is connected to the router. All can access the internet just fine.

-The servers internal (LAN) IP is static, and just outside the range of the DHCP LAN IP addresses; as to prevent conflicts with other computers grabbing that IP as well.

-The WAN IP address for all computers on my network is dynamic; and the WAN address for all computers is the exact same (I'd imagine it's actually the routers IP address, then the router forwards requests on to the appropriate computers using the port forwarding setup as a guide).

-The ISP (Charter) doesn't allow web servers, but generally I have no problems setting up forwarded ports to use for various other applications.  I also tried to contact them about a commercial connection, but the customer service was worse than any I've ever experienced, couldn't even find out if they *offered* one without needing to get all of my account owners information.  It was like walking into McDonalds and asking if they have milkshakes, then they reply "To give you this information I'll need your phone number, full name, address, and last 4 digits of your social security number".



Anyway, thanks for any and all help in advance,
Paul Plusa
(friend of RegnumImbrium)

---

### Post by dreadlord_chris on 2007-08-12
If your ISP doesn't allow their customers to run web servers - they probably enforce this by blocking initial incomming connections to common http ports, *originating* outside the network. What this means is you probably won't be able to run your server on any of those ports.

---

### Post by Frostbain on 2007-08-12
> **dreadlord_chris said:**
> If your ISP doesn't allow their customers to run web servers - they probably enforce this by blocking initial incomming connections to common http ports, *originating* outside the network. What this means is you probably won't be able to run your server on any of those ports.

Any suggested ports to try that wouldn't be considered common?

---

### Post by dreadlord_chris on 2007-08-13
> **Frostbain said:**
> Any suggested ports to try that wouldn't be considered common?
run your server on an uncommon port > 5000 that's not associated with HTTP:
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
Make sure the port(s) you choose gets forwarded from your router & users will have to use the port# in the URL:
i.e. 
If you configure the server to listen on port 42080, then [http://www.somedomain.com:42080](http://www.somedomain.com:42080) would be the URL

---

