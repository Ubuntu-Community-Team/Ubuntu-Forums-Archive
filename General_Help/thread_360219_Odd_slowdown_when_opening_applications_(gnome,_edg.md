---
title: "Odd slowdown when opening applications (gnome, edgy)"
date: 2007-02-12
forum: General Help
---

### Post by Mockskin on 2007-02-12
So my ISP's been a bit rocky tonight, which is rather unusual, but about the same time I started noticing programs taking longer to open (gnome-terminal and some other gnome settings-related things taking upwards of 20 seconds at times).

I'm quite sure it's the ISP and not a local network problem (same connection bumpiness with other comps on the network, both linux and windows, for the record), and I'm not getting the same slowdown in a relatively new xubuntu edgy install on my other comp.

The timing made me little suspicious, and after checking around through processes, rebooting, etc, nothing seemed to correlate to the launch slowdown...

...until I disabled my ethernet card (normal cat5, no wireless goofiness) in network options. After that, things open as quick as normal. Reenable the eth0 card and they start taking longer. 

Maybe I'm misguided, and I'm not extremely concerned as the connection should smooth out sometime in the near future, but I would like to know if this is true, and if not, what else could be causing it.

If it is, are there any methods to avoid the problem in the future? I don't like the idea of connection trouble affecting desktop behavior like that. I'd assume it's a name resolution problem, as they do eventually open (I'd suppose after the resolution timed out).

---

### Post by dcstar on 2007-02-13
> **Mockskin said:**
> 
.........
If it is, are there any methods to avoid the problem in the future? I don't like the idea of connection trouble affecting desktop behavior like that. I'd assume it's a name resolution problem, as they do eventually open (I'd suppose after the resolution timed out).

You shouldn't really have any problems unless your /etc/hosts file no longer references your own system.

Check it and make sure it has entries for localhost, your system nane and the correct local IP addresses.

---

### Post by Mockskin on 2007-02-13
127.0.0.1 localhost
127.0.1.1 glycerine.homenet

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Edit: Set up dnsmasq and that seems to be an effective workaround. Still seems like a design flaw to allow external factors to determine key factors on the local box, unless I'm still misguided about the whole thing.

---

