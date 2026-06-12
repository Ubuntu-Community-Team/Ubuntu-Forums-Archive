---
title: "samba shares browse gone after winbind install"
date: 2007-07-29
forum: General Help
---

### Post by reckless2k2 on 2007-07-29
i'm running kubuntu 7.04 and i can't seem to navigate samba shares through konqueror after winbind install. 

i use to be able to go system menu > remote places > samba shares > workgroup > and then view all my samba shares. since installing winbind, i can't seem to view my workgroup at all. i can see the workgroup but when i drill down to it the error says "time out on server" and it will not show anything. i can still smbmount and such but i'm unable to view the available shares through the konqueror scan. i think it's related to the recent winbind install so i can ping hostnames. could that be the issue?

any help would be appreciated.

---

### Post by kidders on 2007-07-31
Hi there,

To be honest, I wouldn't recommend going down the winbind road, unless you want something more from it than simply being able to ping boxes by hostname (eg authentication, handling domain membership, SID resolution, etc). There are far better ways of achieving that effect that don't involve tinkering with Microsoft networking, which is such a complicated little monster it's almost a science in itself! The alternative is to read up on winbind, and configure it properly, so it doesn't tangle your network up in knots.

Basically, I'm not sure whether to just say "uninstall winbind", or ask for more details about your network infrastructure & Samba configuration.

Depending on what you have, the cleanest solution to your name resolution problem might be DNS, which you could tie into your DHCP, if you wanted.

---

