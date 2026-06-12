---
title: "firestarter, qbittorent problems"
date: 2008-01-05
forum: General Help
---

### Post by CJCorcoran on 2008-01-05
Hello:

I am using firestarter to configure iptables.  I set up a rule in the allow service tab for bittorrent using ports 6881-6889.  However, even with this new policy, the qbittorrent says that I'm still behind a firewall.  I have tried this w/ a few other bittorrent clients, all of which say the ports are closed too.  Anyway way to solve this problem?

--Chris

---

### Post by chrisgibbs on 2008-01-06
Gday,

Have you made sure that the ports have been forwarded to your Ubuntu machine from your router? A quick test is to fire up your bit-torrent client and then jump onto the Shilds Up page to do a quick port-scan [http://www.grc.com/x/ne.dll?bh0bkyd2](http://www.grc.com/x/ne.dll?bh0bkyd2) 

If the above rules that the ports are closed, try shutting down Firestarter briefly and running the same check as above, this will at least determine if it is Firestarter or your Router.

Cheers,

---

### Post by CJCorcoran on 2008-01-06
It can't be my router because I have the firewall on the router disabled.

---

### Post by chrisgibbs on 2008-01-06
The ports on your router will still need to be pointed somewhere; otherwise connecting clients will just try and create a socket to your Routers WAN IP. 

Either forward the ports you require through to the Internal network or if your router supports it you may wish to forward all the ports for your WAN IP to your Ubuntu computer.

I still think you should try the steps i mentioned before to rule-out your router from the equation.


Cheers,

---

