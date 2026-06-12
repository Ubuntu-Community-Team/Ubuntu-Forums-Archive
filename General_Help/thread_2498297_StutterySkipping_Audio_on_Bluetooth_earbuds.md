---
title: "Stuttery/Skipping Audio on Bluetooth earbuds"
date: 2024-06-07
forum: General Help
---

### Post by amalgorithmz on 2024-06-07
not a xubuntu user myself (i use manjaro myself, though i have used ubuntu for a few months myself when i first switched to linux), but helping a friend switch from windows to linux and gave them xubuntu as their first distro
their bluetooth earbuds have horrible skipping/stuttery audio, which is not a hardware issue (they work fine on their phone)
ive never had any bluetooth issues on linux, so im completely lost on how to help them here. any and all advice is appreciated :)

---

### Post by currentshaft on 2024-06-07
Are they using WiFi? 2.4 Ghz or 5 Ghz networks?

Use "ip a" to get the interface name, then:

iwlist wlp2s0 channel | sed -n '/Current/ s/.*://p'

---

