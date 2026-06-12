---
title: "Samba &amp; Winbind - using LDAPS"
date: 2017-12-29
forum: General Help
---

### Post by gibsonfirebird12 on 2017-12-29
Hello,

I have an Ubuntu 14.04 server joined to a 2012 R2 domain using Winbind. All seems to be working just fine.

```
wbinfo -t
checking the trust secret for domain TIMDOMAIN via RPC calls succeeded
wbinfo -g
winrmremotewmiusers__
domain computers
domain controllers
schema admins
enterprise admins
cert publishers
domain admins
domain users
domain guests
group policy creator owners
ras and ias servers
allowed rodc password replication group
denied rodc password replication group
read-only domain controllers
enterprise read-only domain controllers
cloneable domain controllers
protected users
dnsadmins
dnsupdateproxy
linux-admins
```

I'm looking now to use LDAPS for encryption between the Linux client and Windows AD. I have LDAPS enabled on the DC and have tested it using ldp.exe. 

What steps do I need to take to get it working exactly? I've been googling around and can't seem to find any solid info.

---

