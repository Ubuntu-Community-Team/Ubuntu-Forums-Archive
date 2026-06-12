---
title: "Gateway Cannot Be Reached!"
date: 2007-05-17
forum: General Help
---

### Post by xbroscenax on 2007-05-17
Just got passed the Virtual Disk hang, and encountered another problem. A red screen appears saying that the Gateway I have entered cannot be reached and to check my IP. I use a wireless desktop card for my internet connection and have no idea in the leats on how to correct this problem. I had also try to find posts about this particular problem but came up empty handed.

---

### Post by ago on 2007-05-18
Run wubi, before rebooting edit c:\wubi\install\preseed.cfg
You will find a section with network informations with IP numbers. You can put your actual IP/gateway/essid in there. Then reboot.

---

