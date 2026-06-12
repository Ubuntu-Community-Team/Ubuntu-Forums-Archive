---
title: "Firewall Blues"
date: 2007-11-08
forum: General Help
---

### Post by Haruhara on 2007-11-08
Not sure if this belongs here or in the "Absolute Beginner Talk" forum...

I'm using Feisty Fawn, and whenever I try to run aMule or Azureus, the program insists it's behind a firewall.

I have set up my router for port forwarding. My windows machine runs Azureus fine with it, so I've assumed I've set up the port forwarding properly. I have also configured iptables as per the instructions on the [Azureus wiki]("http://www.azureuswiki.com/index.php/NAT_problem") and the [aMule wiki]("http://www.amule.org/wiki/index.php/Firewall"). Both Azureus and aMule complain that the ports they require are closed. The aMule "test ports" thingummy claims the TCP port I had opened was closed.

I tried to plug my computer's ethernet cable direcly into the modem instead of the router, so I could see if the problem was with the router's firewall instead of the computer's.  When the computer was plugged directly into the modem, I couldn't get any internet. Is there some step I'm missing here?

Any help is appreciated. Thank you.

---

### Post by timcredible on 2007-11-08
why did you work on iptables?  there's no firewall running by default on feisty.  did you install one?

also, make sure you're getting the same ip address in feisty that you do with windows, since port forwarding is based on ip address.  ipconfig in windows, ifconfig -a in linux.

---

### Post by LizardKing73 on 2007-11-08
It might be the router itself not allowing access for some odd reason, sounds strange I know but I have 2 routers, one has no problem with Windows but wont even allow Ubuntu (I'm running Gutsy) online....yet it had no problems with Fedora 7.
My second router hooks Gutsy right up.
Different situation I know but still might pay to test a different router.

---

### Post by Haruhara on 2007-11-09
Wasn't aware that feisty came with no firewall. Thanks for the tip!

Both ifconfig -a and the router claim my compy's local ip is 192.168.0.102. This was the address I had set up port forwarding for.

I may attempt to use another router, if I can scrounge one up from somewhere. Is there any reason that plugging my computer directly into the modem doesn't work? I'm a bit baffled by that one.

Thanks for the replies!

---

### Post by LizardKing73 on 2007-11-11
> **Haruhara said:**
> I tried to plug my computer's ethernet cable direcly into the modem instead of the router, so I could see if the problem was with the router's firewall instead of the computer's. When the computer was plugged directly into the modem, I couldn't get any internet.

> **Haruhara said:**
> Is there any reason that plugging my computer directly into the modem doesn't work? I'm a bit baffled by that one.

I'm confused as to what u mean by Modem and Router. If u'r using DSL (ADSL) arent they the samething, the phoneline hooks into the modem/router which then hooks into the PC by Ethernet or USB?
What am I missing? Please explain

---

### Post by HermanAB on 2007-11-11
Check to see whether you have firewall rules installed with:
$ sudo iptables -L

If you see three rules and both are ACCEPT, then there is not firewall.  If you get a long laundry list of gobbledygook, then you have a firewall script installed.  Flush all the rules with:
$ sudo iptables -F

Next check your internet connection.  If you are using a Linksys/Dlink/Netgear/Whatever home router, then you have to forward some ports.  See this: [http://www.aeronetworks.ca/azureus-howto.html](http://www.aeronetworks.ca/azureus-howto.html)

Cheers,

Herman

---

### Post by ramjet_1953 on 2007-11-11
Just put put the record straight, Ubuntu does come with a firewall.

It is called iptables, and all ports are closed by default, and your system is secure.

Packages like Firestarter and Guard Dog are not firewalls, but GUI configuration applications for iptables.

Unless you actually need to do port forwarding, you do not need these GUI configuration tools for iptables and things are best left well alone.

However if you do need to do port forwarding, they can help. Also, as previously mentioned, you may need to go into your router configuration.

This is normally done by entering 192.168.1.1 into a web browser. You then need to enter the router's username and password to get into the config menus.

Regards,
Roger :cool:

---

