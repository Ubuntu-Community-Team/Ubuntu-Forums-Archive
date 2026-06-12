---
title: "Xorg and ATi Radeon Mobility 7500: what is the best configuration?"
date: 2005-04-05
forum: General Help
---

### Post by taniwha on 2005-04-05
Hi there,
 I tried many changes in the xorg.conf to optimise the use of my ATI Radeon Mobility 7500 (32MB) and so far it works decently. However, I ask your help: if someone has reached any configuration that allows the best performances with this graphic card, please let me know.
Thanks in advance.
 :-)

---

### Post by thepoch on 2005-04-06
On my laptop I've added

Option "AGPMode" "4"

as it supports AGP 4x. This results in increased framerate when running glxgears (jumped from 500+ to 700+). That's about all I've noticed though.

---

