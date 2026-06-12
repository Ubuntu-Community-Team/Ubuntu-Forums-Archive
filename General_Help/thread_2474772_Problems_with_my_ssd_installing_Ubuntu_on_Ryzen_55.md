---
title: "Problems with my ssd installing Ubuntu on Ryzen 5500u"
date: 2022-05-07
forum: General Help
---

### Post by sebsdnl on 2022-05-07
Guys I have an hp EF-2000 with a ryzen 5500u, I installed ubuntu but every time my pc suspends the ssd disconnects. When i check the log the last entry is suspended cause it can't write anything later.
Even when im on the live cd if I suspends the ssd goes away after a few seconds. I need help.

---

### Post by #&amp;thj^% on 2022-05-07
just to help attract more lookers can you include:
```
inxi -D

```
it will show something like:
```
Drives:
  Local Storage: total: 5.69 TiB used: 31.15 GiB (0.5%)
  ID-1: /dev/nvme0n1 vendor: Western Digital
    model: PC SN730 SDBQNTY-256G-1001 size: 238.47 GiB
  ID-2: /dev/sda vendor: Seagate model: ST1000LM049-2GH172 size: 931.51 GiB
  ID-3: /dev/sdb type: USB vendor: Western Digital
    model: WD My Passport 2627 size: 4.55 TiB
```
EDIT: the suspend issue comes from a wayland session, see if there is a better response on a X11 session
```
inxi -C
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1612 min/max: 1400/3000 cores: 1: 3822 2: 1396 3: 1434
    4: 1394 5: 1384 6: 1551 7: 1397 8: 1397 9: 1396 10: 1397 11: 1397 12: 1389


```

---

