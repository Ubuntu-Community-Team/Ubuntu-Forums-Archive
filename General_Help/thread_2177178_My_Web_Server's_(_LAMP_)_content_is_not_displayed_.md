---
title: "My Web Server's ( LAMP ) content is not displayed on other systems"
date: 2013-09-27
forum: General Help
---

### Post by Greymtr on 2013-09-27
Hello All ,
     I'm currently running a webpage on Ubuntu 12.04 LTS Web Server edition ...... I have setup all necessary software ( at least I think so ) & I'm running a LAMP infrastructure.

From my computer I can access the page typing in ```
localhost
``` the same thing happens when I type in my computer's IP address.

When I want to access my computer from elsewhere from another computer not connected to the same internet line , I'm not able to do so by typing my IP address .... what must I do to do this ?

Thank you in Advance for all solutions.

PS : The IP address I'm talking about is my LAN address ( the 192.168. one )

---

### Post by shiraz dindar on 2013-09-27
1. Make sure you've forwarded port 80 on your router to your internal LAN IP address.

2. Chances are you are on a dynamic IP. You would then need to use a dynamic DNS service. 

For testing purposes you can just do #1 first and then try to hit the IP from an outside address, given you retrieve your outside world (not internal) IP address from your computer via a service like whatsmyipaddress.org. Once you've got that done, you'll want to set up #2.

---

### Post by Lars Noodén on 2013-09-28
To add to that, to be able to connect to your machine from a remote location, you need to know your router's current external IP address.  That's in addition to having the right ports forwarded.   If you check manually you can find your external ip using a services like Canyouseeme: [http://canyouseeme.org/](http://canyouseeme.org/)  Now in most cases, if your ISP has you on DHCP, that external address will change from day to day.  

One way around that would be to register with a [dynamic DNS service](https://help.ubuntu.com/community/DynamicDNS) which would give you a permanent hostname.  That would require some additional changes in your router, but most routers support those services.

---

### Post by Greymtr on 2013-09-29
All right , I registered with a Dynamic DNS service and now have a Dynamic DNS , I've forwarded my ports to 80 , yet when I try to access the host , provided to me by the service , there is an error.....Any idea what went wrong ?

PS : I've also updated my modem features.

---

### Post by Lars Noodén on 2013-09-29
Be sure to double check the ip number, compare what the Dynamic DNS says it is with what the modem actually has.  They'll eventually sync up but it is possible that they are out of sync.

Also, is your modem/router such that you can access the external IP properly from wihtin the LAN?  You may have to try connecting from an outside machine for the port to be forwarded correctly.  

When you try to connect now using HTTP on port 80, what error message are you getting?

---

