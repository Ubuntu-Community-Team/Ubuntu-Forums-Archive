---
title: "Wireless here yesterday...gone today"
date: 2006-10-25
forum: General Help
---

### Post by webb3201@airmail.net on 2006-10-25
I had an absolutely perfect install on a T40 Thinkpad this weekend.  All went well and the machine performed flawlessly in every way.   I am connecting to my airport router, which worked like a champ right out of the box.  

I took the machine to work today and connected via cable.  My problem is that now that i am back home, I cannot get connected to the wireless network.  The machine sees the signal, but I cannot get anything to actually work (browser errors etc).  

Any nice utilities or troubleshooting steps?

---

### Post by wieman01 on 2006-10-25
You did not configure your firewall in the meantime?

Please do this for us while the ethernet cable is unplugged (from command line - post the output):
> sudo /etc/init.d/networking restart
> route
> sudo gedit /etc/network/interfaces
> iwconfig
> iwlist scan

---

### Post by CheshireMac on 2007-07-17
> **wieman01 said:**
> You did not configure your firewall in the meantime?

Please do this for us while the ethernet cable is unplugged (from command line - post the output):
I'm working with the same issue, except that I don't have the option of connecting my laptop via wire . . .I'm running with a 2200 card, and I think maybe the problem in in the interfaces log . . .my essid is always named "netgear" because I entered it into the configurations, and it wouldn't go away . . .what should a default interfaces log look like? 
Also, if that's not the issue . . .what is? ~LOL~ I've been through god knows how many different How-Tos with no avail. Any help would be fantastic.

---

