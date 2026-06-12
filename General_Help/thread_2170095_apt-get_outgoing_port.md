---
title: "apt-get outgoing port"
date: 2013-08-24
forum: General Help
---

### Post by SchnappiJedi on 2013-08-24
Hi,

I was tasked with building a Linux server in a corporate environment that utilizes all Windows servers up until this point. When trying to use apt-get the update/install fails (and I can't recall the error off the top of my head). We know that it is a firewall issue and we are trying to open up the firewall. But we can seem to figure out which port apt-get is using.

Does anyone know what outgoing port apt-get is using?

---

### Post by Cheesemill on 2013-08-25
Apt-get just uses http to download from the repositories so it uses exactly the same ports as you'd need to access web pages.

That is the connection is made from a random high port to port 80 on the mirror you are using. If you wanted to be more specific you could find the IP of the mirrors you are using and only allow outgoing traffic to port 80 to that specific machine.

---

### Post by SchnappiJedi on 2013-08-25
Port 80 is obviously open...but we still can't use apt-get. I am thinking it may be something specific to the Barracuda firewall (aka a setting blocking this type of port 80 traffic) because I can't think of any other possible reasons.

*Can you clarify your statement about "a random high port." If I understand you correctly than a "random high port" (outgoing) is needed to use apt-get. If this is the case it would make sense why apt-get is blocked as only certain outgoing ports are allowed through the firewall.

As with most things computer related the simplest things are what slows things down the most and causes the most headaches!

---

