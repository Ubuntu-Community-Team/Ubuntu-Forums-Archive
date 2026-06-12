---
title: "getting kicked off internet every couple hours"
date: 2016-03-26
forum: General Help
---

### Post by contra2 on 2016-03-26
not sure if this is the right spot but here goes

I get kicked off the internet every so often (about every two hours)
and I don't really know why. When I used to use windows or Ubuntu 14~, no problem but with this 15~ I am

anyone else have this problem and found a fix? 
[CENTER]My system:

[B][COLOR=#ff0000]
 [/COLOR][/B][CENTER][B][COLOR=#ff0000][FONT=Tahoma]AMD Athalon II X4 630 2.8, ASUS M5A99X EVO R2.0,
GeForce GTX 960 4G, G.SKILL Sniper 16GB DDR3 1600, 512 Mushkin SSD, LG Ultra Wide 29"[/FONT][/COLOR][/B][COLOR=yellow][FONT=Tahoma]
[/FONT][/COLOR]**[COLOR=#ff8c00][FONT=Tahoma]Ubuntu 64 bit[/FONT][/COLOR]**[/CENTER]
[/CENTER]

---

### Post by pqwoerituytrueiwoq on 2016-03-26
What NIC are you using?
```
echo "$(lsusb)$(lspci)" | egrep -i "ethernet|wireless"
```

---

