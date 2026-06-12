---
title: "Vpn not working Ubuntu 20.04"
date: 2022-03-15
forum: General Help
---

### Post by joneydkh on 2022-03-15
I run vpn(PPTP and openvpn neither makes any difference) on my Ubuntu.

In my country some sites like telegram ,youtube or twitter are blocked and I have to run a vpn to access them.

So after I run the vpn , telegram-desktop works well but the browsers do not work and all blocked site like youtube still can not be accessed but the normal sites can be accessed.

The VPN does not allow access to any of the blocked sites when I use a browser.

when i use both pptp and nordvpn firefox extension vpn is working fine and my ipv 6 is Not detected and ipv4 is not my real ip but when i use pptp without extension its only changing my ipv4 and ipv6 is my real ip and vpn is not working. how can fix this problem

---

### Post by TheFu on 2022-03-15
PPTP shouldn't be called a VPN. It has been cracked since 2005. It is much more like a proxy, but with terrible encryption.
NordPVN using either openvpn or wireguard should be fine.  I'd be certain to setup AES256, not the default AES128 too.

I don't use IPv6, so cannot say anything about it.  This is because I'm not confident in my ability to securely use it.  IPv6 does have an IPSec VPN built into the protocol. Perhaps that could be used?

Saying something doesn't work leaves out the technical facts necessary to figure out the issue.  Can you please post those?

---

