---
title: "RoadRunner Problems"
date: 2006-12-23
forum: General Help
---

### Post by branhow on 2006-12-23
hey everyone, i've been a member of the forums for a while trying to get to know ubuntu a little better. I've been a Mac user most of my computer life but I have one PC and it had Windows XP on it. I hate windows with a passion because of all the problems with it, so I reformatted it with Ubuntu. I love it! the only problem is I cannot access the internet now. The computer is a Compaq I got in 2000 so it's pretty old. I'm pretty sure the eternet card is working. It's a PCI ethernet card. Anyways I'm using a Motorola Router and a Linksey WIFI Router. I got the compaq plugged into the WIFI linksey via ethernet cable. Oh, and I'm using RoadRunner for my internet services. Does anyone have any ideas? Please I am in need of the internet on this computer! thanks a bunch guys and gals! 

PS I got the latest version of Ubuntu running on it, even though its really slow booting up.

---

### Post by BrendanM on 2006-12-23
So you have the Linksys router behind the Motorola router? Which one is connected to your cable modem? Are you able to get an IP address? You might want to try "sudo dhclient" and see what kind of output you get there.

---

### Post by esaym on 2006-12-23
What does ```
ifconfig
``` show?

---

### Post by branhow on 2006-12-23
the motorola modem is plugged into the linkseys and then the linkseys into the computer. i also tried directly pluggin it into my motorola. where do I find that program? is it on the installation disc? i checked the properties from the ethernet and its seeing the router because it says rr.nc.com and localhost and some other stuff like that

---

### Post by esaym on 2006-12-24
> **branhow said:**
> the motorola modem is plugged into the linkseys and then the linkseys into the computer. i also tried directly pluggin it into my motorola. where do I find that program? is it on the installation disc? i checked the properties from the ethernet and its seeing the router because it says rr.nc.com and localhost and some other stuff like that

"ifconfig" is a command typed in the console.  It will display what all network interfaces are up (if any)

---

### Post by TransitMan on 2006-12-24
If you are plugged into your Linksys router, then you need to access your network propertiers under Ubuntu.
Once there, you should find you network card. 
In the settings, you need to put the following,
check use this IP address: 192.168.1.20
Subnet: 255.25.255.0
Gateway: 192.168.1.1
Apply settings, then find the DNS entries.
Put the following for DNS: 192.168.1.1 and 4.2.2.6
Apply settings, then try and browse the router at 192.168.1.1.
If you get a login pop-up, then clear the address bar, and input a web address, [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)
If your Ubuntu network properties is setup correctly, you should wind up back here at the forums.

---

