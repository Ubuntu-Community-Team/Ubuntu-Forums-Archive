---
title: "Connecting to a PPTP VPN"
date: 2012-11-27
forum: General Help
---

### Post by CrusaderAD on 2012-11-27
I'm able to connect to a PPTP VPN just fine with Ubuntu 12.04 but once I connect, I cannot browse anything. No shared drives or anything. Any ideas on how to troubleshoot this?

---

### Post by rai4shu2 on 2012-11-27
VPN gives you an open connection to the internet, so you should be able to find anything that its DNS lets you find. If you're using UFW (or any form of firewall), double-check your settings to be sure you aren't neglecting some detail there. If you aren't setting up a firewall, then I would strongly suggest it.

---

### Post by CrusaderAD on 2012-11-27
Thanks for the reply. Do you happen to know exactly where to plug the DNS (IP) setting in with Ubuntu? I've been given a DNS ip to use, but not sure where to enter it.

---

### Post by rai4shu2 on 2012-11-27
I think DNS is set in IPv4 or IPv6 settings, the same as normal, only the traffic is routed (mostly) through the VPN.

see: [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by dcstar on 2012-11-28
> **CrusaderAD said:**
> I'm able to connect to a PPTP VPN just fine with Ubuntu 12.04 but once I connect, I cannot browse anything. No shared drives or anything. Any ideas on how to troubleshoot this?

Are you referring to Shared Drives on the VPN connection or losing access to existing Shared Drives when the VPN is connected?

---

### Post by CrusaderAD on 2012-12-03
I was referring to shared drives on the VPN (not local drives). Since I couldn't "browse" for shares, I ended up mapping them via their local IP and folder name. That worked. I can access shared devices provided I know the IP address.

---

