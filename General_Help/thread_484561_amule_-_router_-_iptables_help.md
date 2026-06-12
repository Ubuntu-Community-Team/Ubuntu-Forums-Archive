---
title: "amule - router - iptables help"
date: 2007-06-25
forum: General Help
---

### Post by southernman on 2007-06-25
Think I screwed the pooch this time!

Events that occured:

Setup amule, but kept getting lowID.

Installed Firestarter, but not able to make it work right. MY fault I know.

Managed to add *iptables -A INPUT -p tcp --dport XX -j ACCEPT* and one for udp port so that amule would get a highID. Success - Everything worked fine for the last 5 days or so and then the router played punk and had to reset it. Shouldn't be a problem, but now when I restart my ubuntu machine, the router assigns a new ip via dhcp. Not thinking clearly after chasing my tail for about two hours, I did a *iptables -F INPUT* or something similar and reopened the two ports in iptables again. Needless to say, I am not having any luck getting amule running with a highID again. Testing the ports shows 4662 unreachable.

My plea is to find out if this is an issue with:

1 - Router?
2- Computer grabbing a new DHCP IP each reboot?
3- Did I really foul up with the iptables -F INPUT thingamajig?

Please help if able.

I am considering a reinstall and I know that this can be fixed... most likely easily! I just can see the forest for the trees atm.

Thanks in advance!


Did removing the input rules

---

### Post by testube_babies on 2007-06-26
iptables would allow your amule connections on a default Ubuntu install, so I'm guessing your router is the culprit.  Find info on how to allow port forwarding or how to set up a DMZ, and hopefully that will solve your problem.  DHCP shouldn't be a problem, either.

It should also be noted that amule uses three ports (what for?  i have no idea).  4662, 4672, and another usually TCP+3 (4665).

EDIT:  I just found this page which should also help you out: [http://www.amule.org/wiki/index.php/Get_HighID](http://www.amule.org/wiki/index.php/Get_HighID)

---

### Post by southernman on 2007-06-26
> **testube_babies said:**
> iptables would allow your amule connections on a default Ubuntu install, so I'm guessing your router is the culprit.  Find info on how to allow port forwarding or how to set up a DMZ, and hopefully that will solve your problem.  DHCP shouldn't be a problem, either.

It should also be noted that amule uses three ports (what for?  i have no idea).  4662, 4672, and another usually TCP+3 (4665).

EDIT:  I just found this page which should also help you out: [http://www.amule.org/wiki/index.php/Get_HighID](http://www.amule.org/wiki/index.php/Get_HighID)

Thanks for the trouble you went through! *shakes hand* 

I had the ports setup in my old antique Linksys BEFSR41 v.2 router - prior to the problem and afterward. Prior to the problem I kept getting lowID, until I did the input rule from the link you found... once I setup the input rules for 4662 tcp, 4672 udp, and 4665 udp, the highID came.

I concur that it's the router. I think it got to hot and reset itself. It does have the latest firmware, but it's from 2004.

Left amule running while at work today, with a lowid. I just restarted amule, and viola the highID is back.

Going to see if I can research a good replacement router... probably another LInksys. 

Thanks again for your trouble.

:)

---

### Post by southernman on 2007-06-27
Here are some things I've done - been a long evening!

Tried a pci nic card. Thought maybe my onboard nic was flaking out. I don't think it was the issue in the end.

Disabled Roaming mode in the network manual configuration gui. I first tried Auto DHCP, but still kept getting a new IP from the router after each reboot! Fixed this problem be setting the configuration to a static IP using the current IP from DHCP of the router. The IP has stayed the same... WoW - whooda thunk it! Not to bad learning for an ole blue collar guy like me! :p

Setup amule to use port 1720 tcp, 4672 udp, and 1723 udp... instead of using 4662 & 4665. Do ya think ma bell (my isp) could ever reduce itself to throttling??? Of course they would! NO proof but it's almost a given with the popularity of P2P these days.

Still had loss of connection issues after all this. I am almost certain most of the blame with that lies on the Kad side of things. After reading countless pages of forum pleas for help with the same problem, most had stopped using kad which solved their problems. For the last hour, I've not lost the server connection.

I'll post back tomorrow, hopefully to confirm continued success.

---

