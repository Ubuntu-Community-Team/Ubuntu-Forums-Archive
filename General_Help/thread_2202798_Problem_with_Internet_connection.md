---
title: "Problem with Internet connection"
date: 2014-01-31
forum: General Help
---

### Post by lotharlorraine on 2014-01-31
Hello, I have a weird problem which has come up times and times again after I've installed Ubuntu on my computer.

During the two next weeks, I have no difficulty using the Internet.

But then it no longer works. 
While the connection seems to work perfectly (as indicated in the upper right part of the screen), all the internet browsers no longer work and are no longer able to find any page at all. 

BUT if I use Shrew for getting a VPN connection it works and then it become possible to use the browser without problems. 

What is the cause for this?

Does it mean that my computer is hexed?

---

### Post by dargaud2 on 2014-01-31
Try to see if the problem is with your DNS (nslookup [www.google.com](www.google.com)), with your router (ping 192.168.1.1; traceroute [www.google.com](www.google.com)), with your browser (wget -O- [http://www.google.com/](http://www.google.com/))...

---

### Post by grahammechanical on 2014-01-31
The Network Manager icon in the top panel will tell us when we have an connection to the router. It will also tell us when that connection is broken. But what happens when the router drops it connection to our Internet Service provider (ISP)? We get a message about a service called Avahi being disabled.

Is your router dropping its connection to the ISP? My router was doing this the other day and I got the same problems as you. The ISP may being doing maintenance to its servers or may have some other problem that is causing poor quality service to its customers.

Regards.

---

