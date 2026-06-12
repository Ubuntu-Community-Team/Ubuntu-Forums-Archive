---
title: "Web hosting with SIM card"
date: 2015-09-25
forum: General Help
---

### Post by Tichun on 2015-09-25
Hello, folks. I feel the need of hosting a website (PHP etc.) The problem I encounter is that the only internet option for me is 3/4G and for which I use SIM card that I've put into USB stick which is plugged into a router. Localhost works for my  local computers but setting  port-forwarding on router website gives no results. USB stick has no option to port-forward on its webpage.  1) How can I host?  router dwr-116 dlink usb lte stick huawei

---

### Post by TheFu on 2015-09-26
I've never heard of any cellular data plan that allowed inbound ports over the internet. Never.
Sorry.

With that said, you can check if your WAN IP is even internet "routeable" by determining the WAN IP.  Log into the router and see what the WAN IP is - if it is NOT a "private address" ... [https://en.wikipedia.org/wiki/Private_network](https://en.wikipedia.org/wiki/Private_network) we can try some other things. There isn't much hope, really.

---

### Post by Tichun on 2015-09-26
It is private (10.0.0.0 - 10.255.255.255).

---

### Post by TheFu on 2015-09-26
> **Tichun said:**
> It is private (10.0.0.0 - 10.255.255.255).

There is the answer. You cannot host any services on the internet with a private WAN IP. Sorry.

Well ... there is away, but you need a server on the internet to do it. Got one or will you get one?

---

