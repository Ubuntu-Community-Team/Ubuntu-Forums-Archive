---
title: "Connection dies"
date: 2006-11-09
forum: General Help
---

### Post by k_smolka on 2006-11-09
Hi all 

I have placed several posts now about problems with WPA and network manager in edgy. In dapper my enterprise wpa connection worked perfectly, after upgrading to dapper  the connection keeps dropping.

I have tired installing the latest network manager with no success.

Can any body offer any help.

1) Do people this this is likely to be a problem with network manager? 

2) Can I down grade network manager?

3) Can I access a wireless wpa network via manual commands 

any help would be most appreciated. 

Regards 

Karl

---

### Post by jpeddicord on 2006-11-09
What brand is the card? If the chipset is Atheros (D-Link and others), then it most likely is this unresolved bug:

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/66176](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/66176)

---

### Post by k_smolka on 2006-11-09
Its a intel pro wireless

Currently using the ipw22o driver

Weird thing is that it was working on dapper but dies on edgy.

---

