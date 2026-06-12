---
title: "[SOLVED] screen resolution"
date: 2008-07-09
forum: General Help
---

### Post by pedrom169 on 2008-07-09
when i first ventured into ubuntu i used it ubuntu 7.10. When i used this version and installed the nvidea driver i could get the resolution of 1280 x 1024. Yesterday when i installed ubuntu 8.04 and installed the nvidea driver i can only get 1024 x 768.

Is there a simple fix for this

Cheers
Peter

(I am not at my ubuntu pc, im at work so any instructions ill try out when i finish at work)

---

### Post by rogier.de.groot on 2008-07-09
It'll probably be the damn auto-detection again... If you happen to have your old xorg.conf around, try replacing the new one with that. The new xorg.conf doesn't list supported resolutions and such, it auto-detects them, which goes wrong sometimes. Using old xorg.conf's is the only solution I've found to work, though there are undoubtedly others...
The old screen configuration tool is still in Ubuntu, it's just hidden in the menu; you can unhide it from the menu editor in preferences. Not that it ever did me good; in my opinion the damn thing sucks, but hey YMMV.

---

### Post by Hairy_Palms on 2008-07-09
one way that always works for me, install nvidia-settings and use that to change the resolution.

---

### Post by pedrom169 on 2008-07-09
thank you for your help so quickly as this was my only problem in ubuntu atm (even got my wireless working haha) :)!
i will try both of these when i get home and post results.

---

### Post by pedrom169 on 2008-07-09
thank you so much. nvidia-settings worked like a charm.
cheers mate

---

