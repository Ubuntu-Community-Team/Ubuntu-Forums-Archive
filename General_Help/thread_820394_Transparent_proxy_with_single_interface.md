---
title: "Transparent proxy with single interface"
date: 2008-06-06
forum: General Help
---

### Post by barrowdene on 2008-06-06
Hi all,

Can anyone firstly tell me if it is possible to setup a transparent proxy server with squid and dansguardian use only one interface ?
If so how do I do this ?

Thanks
Jim

---

### Post by CyberAxe on 2010-12-21
Did you ever find out? or get it setup?

I find it annoying so many posts get un replied to.

I've been trying to set this up at work today (just squid not dans guardian), but after appling the IPTables rules and several variations i've found it will only work with the local webserver so its pretty much the reverse of what i want (though obviously i need to mess with squid settings to stop it cacheing local server)

From what I've gatherd the IPTable rules that keep popping up will only work with 2 interfaces 1 for lan and one for wan, which is annoying even though i eventually plan to have multiple interfaces setup i'd like to get this working first.

---

### Post by CyberAxe on 2010-12-21
I just found this post which looks promising, all other examples have had pre and post routing but not the forward rule so this looks like what is needed.

[http://tldp.org/HOWTO/TransparentProxy-6.html]("http://tldp.org/HOWTO/TransparentProxy-6.html")

---

### Post by dandnsmith on 2010-12-21
The lack of replies usually indicates that no-one wants to stick their neck out with a totally unfamiliar topic.

In this case - longer ago than I started looking at these fora in any detail - I could comment that the difficulty with the single network card might be got round by using two (or more) virtual interfaces on the one card, each with it's own IP address.

Please don't ask me how to do it, as I merely remember comment from people saying they had done it (under linux/Unix), but wasn't sufficiently interested at the time to get the detail of how to do it. This method does mean you have a more complicated set of routing rules, but does give some added flexibility.

---

### Post by CyberAxe on 2010-12-21
Thanks for the suggestion, I already have several Virtual Interfaces setup, in theory I should just need to NAT route between them but obviously thats over simplifiing it and I've yet to delve into NAT Rules.

---

### Post by dandnsmith on 2010-12-21
After a bit of googling a couple of minutes ago I came across [this page](http://wiki.openvz.org/Virtual_Ethernet_device), but it looks like you've got that bit covered already.

Good luck

---

### Post by CyberAxe on 2010-12-22
Heh I stupidly realised that it was in fact working, all I needed to do is set the Server running Squid as the gateway.

Did not need a second interface or fancy rules, just the basic port routing.

Hence to answer the initial post it is in fact possible and you just need to make sure the gateway is correct.

---

