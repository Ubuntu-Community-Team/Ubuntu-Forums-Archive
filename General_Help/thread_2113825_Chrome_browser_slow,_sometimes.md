---
title: "Chrome browser slow, sometimes"
date: 2013-02-08
forum: General Help
---

### Post by frenchian on 2013-02-08
Recently, I think, Chrome has slowed down, but it's not ALL the time.

Sometimes, the "rotating circle on the tab" (does that make sense?) goes anti-clockwise and spins for several seconds before I get through to the site - sometimes, I never get through. Other times, though, response is sub-second.

Knowing just enough to meddle, I browsed for a solution. DNS lookup seemed to be the problem , so I did the following:

1. Set the line in /etc/nsswitch.conf to

"hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4"

2. Disable IPV6 by editing /etc/syscntl.conf

Neither brought any noticible improvement.

(The problem might be external. My local ADSL service is overloaded (they're in the process of upgrading the network with fibre-optic, etc) so it could be there.)

Can anyone tell me how to identify and eliminate any internal problems or config errors?

(I'm running Kubuntu 12:04, connecting via ethernet to a netgear router. DNS servers in it are set to Google)

Thanks

---

### Post by csillva on 2013-02-20
Did you follow these instructions to disable ipv6?

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

