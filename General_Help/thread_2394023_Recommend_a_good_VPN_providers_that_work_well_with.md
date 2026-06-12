---
title: "Recommend a good VPN providers that work well with Ubuntu"
date: 2018-06-11
forum: General Help
---

### Post by waltd on 2018-06-11
Hi all,  can anyone recommend good VPN providers that work well with Ubuntu?

---

### Post by Habitual on 2018-06-11
I can't recommend this, but they get mentioned a lot in Reviews from professionals.
[https://nordvpn.com](https://nordvpn.com)

Panama registry.

---

### Post by crip720 on 2018-06-11
Have used both Nordvpn and Windscribevpn. Both easy to setup and work well. Think most good vpns using openvpn would be good.  Using Windscribe now because it has lifetime deals every so often.  Torrentfreak .com has a listing of vpns and what they stand for.  You can go to the vpns sites and see from their support page if they have a linux setup, most do not have a GUI app for Linux, but they still work.

---

### Post by TheFu on 2018-07-04
> **waltd said:**
> Hi all,  can anyone recommend good VPN providers that work well with Ubuntu?

Every few months different security sites post current VPN scorecards. VPNs can change their policies at any point, so this becomes a trust thing more than anything else.  Google should find those pages.  Be certain to limit the results to only withing the last quarter. Things change fast.

A few VPNs have been asked to help govts with data.  I know of one which has told the FBI they couldn't comply with the orders to provide data because they didn't have any data which could be provided.  They've done this multiple times over a year apart.

There are many considerations for which VPN might be best for any person based on what you seek from the provider.  Simple web browsing and email is one thing they all do well enough, though if you use gmail you might find that google doesn't like any VPNs and blocks access to your accounts and their services. It is easier to fire google than give up privacy, IMHO.

If the VPN provider uses OpenVPN then it will work under Linux using the stock VPN tools. You don't need to use their setup script or their client(s). You just need to understand openvpn and get the .ovpn file and setup any certs for the provider you elect to use.  
Any VPN provider still using PPTP should be avoided.  
I'd also avoid VPN providers that don't support 256-bit ciphers and I'd avoid free VPNs because they are being offered for 1 reason - to have access to your data at the exit node.

IMHO.

---

