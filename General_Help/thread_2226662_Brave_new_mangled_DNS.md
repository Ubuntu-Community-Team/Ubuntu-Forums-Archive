---
title: "Brave new mangled DNS"
date: 2014-05-28
forum: General Help
---

### Post by ship22 on 2014-05-28
Ok, I've been a unix man for over 20 years. I don't know what Ubuntu has done to DNS but after avoiding it for many revs I can't take it anymore. WHAT did they do to it and how can I get a clue on how to work with it???

resolv.conf no longer works, the crap in network manager doesn't see to have any affect, dnsmasq doesn't resemble anything I've used it on in other systems.

I'm trying to figure out why I can't resolve hosts when I turn on my firewall, and why dns still doesn't work when I turn the firewall back off... anytime I test something I have to reboot to resolve again. restarting networking doesn't restore it, using the gui to turn network on /off doesn't work...this version of dnsmaq doesn't seem to have any start/stop functions.

How can you take something so incredibly easy like dns and mangle it so badly?  Was editing /etc/resolv.conf REALLY that daunting for potential ubuntu users?

if anyone can toss me a clue here, I'd be grateful.

---

### Post by ship22 on 2014-05-28
After searching for docs about this screwed up design, they're either non-existent or well hidden.

For a "hammer fix":

Edit /etc/NetworkManager/NetworkManager.conf[COLOR=#000000][FONT=Arial] and comment line starting with [/FONT][/COLOR]dns
[COLOR=#000000][FONT=Arial]Edit [/FONT][/COLOR]/etc/resolv.conf[COLOR=#000000][FONT=Arial] as You need.
Move on with life.


[/FONT][/COLOR]

---

