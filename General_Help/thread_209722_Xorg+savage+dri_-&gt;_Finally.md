---
title: "Xorg+savage+dri -&gt; Finally"
date: 2006-07-05
forum: General Help
---

### Post by JackDog on 2006-07-05
I was having a hard time getting my ProSavage8 (S3 Inc. VT8375 [ProSavage8 KM266/KL266)

What ended up working was removing all references to wacom devices. Turned out to be as simple as that. If anyone else has a similar problem, you may want to try removing them as well. This caused X to crash on startup and freeze the laptop. It now works great, although the savage driver is still pretty slow, its way better than vesa =)

---

