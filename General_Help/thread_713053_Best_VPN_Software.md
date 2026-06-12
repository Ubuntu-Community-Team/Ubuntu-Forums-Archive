---
title: "Best VPN Software?"
date: 2008-03-02
forum: General Help
---

### Post by ShinHadoken on 2008-03-02
Ok, now that I have my brand new (=D) wireless router and ethernet switch set up, I'm looking at VPN software. What's the best choice for Ubuntu (7.10)?

Edit: I'm not sure what you mean, pete. I'm running it on a 7.10 Gutsy Desktop box, if that tells you anything.

---

### Post by pete on 2008-03-02
"vpn software" = client or server?

Client-wise, I like vpnc.  It works with my corporate overlords' Cisco vpn system, and integrates nicely with nm-applet.

---

### Post by ShinHadoken on 2008-03-02
Bump

---

### Post by SpaceTeddy on 2008-03-02
i'm a big fan of openvpn. Easy to configure, only needs one port, and can (with some tweaks) be run full in usermode.

[EDIT]
TheCog (next post) mentioned another plus - it goes nicely thought nat AND it can even be figured statefull by iptables (allthough udp is stateless)

---

### Post by The Cog on 2008-03-02
I'm with SpaceTeddy. OpenVPN is very flexible and reliable. A big plus is that it only requires one UDP port and goes nicely through NAT.

---

