---
title: "lspci and xorg"
date: 2007-04-13
forum: General Help
---

### Post by linckraker on 2007-04-13
trying to figure out how to convert lspci output to something readable by xorg.conf 

need to know what the BusID would be if the lspci output is 0:0a.0   i would paste my complete lspci output here but its on a different computer thanks

---

### Post by Austin_KW on 2007-04-13
An example from my laptop
lspci```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 7000 IGP

```
xorg.conf```
        BusID           "PCI:1:5:0"
```

---

