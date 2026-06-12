---
title: "Port Forwarding*#@(*&amp;(@#$"
date: 2007-05-25
forum: General Help
---

### Post by krismatth3 on 2007-05-25
Anyone using ubuntu as a gateway/router?

Anyone have any luck at all getting port forwarding to work?

I've done it by hand with iptables; I've done it using "guidedog" as well.. Neither work on 7.04 - but they both used to work on previous ubuntu releases, and iptables has never failed me on ANY distro.

So what's up?

---

### Post by mbradlcu on 2007-05-25
yes,, 
I"m not sure if this is needed but try:
```
sudo echo "1" > /proc/sys/net/ipv4/ip_forward
```

---

