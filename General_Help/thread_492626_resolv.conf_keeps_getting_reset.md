---
title: "resolv.conf keeps getting reset"
date: 2007-07-04
forum: General Help
---

### Post by davisford on 2007-07-04
Hi, I installed Ubuntu 7.0.4 on Mac OS X VMWare Fusion.

Mac OS X host connects to VPN.

Booting up Ubuntu in VM, I can also use VPN, but to get DNS to work on internal VPN hosts, I have to add internal DNS nameserver entries.

I tried editing /etc/resolv.conf directly.
I tried using System -> Administration -> Networking to add DNS nameservers

Both work (for a while).  Probably 5-10 minutes pass, and something overwrites the /etc/resolv.conf file with the default DHCP served DNS nameserver, so my VPN host lookups fail.

I figure this might happen on a reboot - when the network scripts run, but not after 5 or 10 minutes of use.  I wouldn't think DHCP lease would be that short.

Any ideas on how to fix?

---

### Post by testube_babies on 2007-07-04
Here's one way (of many) to do it:

Set up resolv.conf the way you want it, then
```
sudo chattr +i /etc/resolv.conf
```

This will make the file immutable, meaning not even root can change it.  If you need to change it again, do a 
```
sudo chattr -i /etc/resolv.conf
```

---

### Post by davisford on 2007-07-04
thx, i set that -- will see how it works.

q: any idea what the root cause of this is?

---

### Post by kuja on 2007-07-05
davisford: It's supposed to do that. There should be another file you can edit somewhere to force a certain nameserver to always be in it though, I think it would be in the /etc/resolvconf/ folder, but I can't remember as my setup for it's modified by quite a lot (using dnsmasq mostly for dns caching, and it messes with resolvconf.d)

---

