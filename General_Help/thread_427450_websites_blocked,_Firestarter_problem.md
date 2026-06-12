---
title: "websites blocked, Firestarter problem?"
date: 2007-04-29
forum: General Help
---

### Post by mock47 on 2007-04-29
I now have a problem when browsing the web.  Some sites no longer
respond and eventually  time out.  Two examples are eBay and my government
TSP site (tsp.gov).  There are many others.  Always in the past I could surf at
will. In fact I needed to move to my wife's machine to post this request for help! 
( i could view and write it on mine but it would not send.)

Prior to this occurance  I installed firestarter.  Thinking this could
be the problem, I tried disabling Firestarter. No change. I have since
removed, reinstalled and again removed Firestarter.

I have cleared the iptables with sudo iptables -F and the command sudo
iptables -L yields the following:

art@art-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
art@art-desktop:~$

The blockage continues.

To complicate matters I had recently been having service breaks with my
dial-up ISP.
I have been unable to determine whether the problem is with my machine
or the ISP.

Any ideas?

---

