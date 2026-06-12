---
title: "user switching (lightm) causes mouse to float"
date: 2020-12-27
forum: General Help
---

### Post by 16kzx81-1980 on 2020-12-27
Where  'switch user' us is selected, the screen drops to lightdm, then mouse 'floats/drifts'. This is not phantom movement - its move the mouse in any direction and it overshoots, like its accellerated. Makes it impossible to accurately click on anything without moving it super slowly. The issue carries across to the new login, and we have to  restart the machine each time to resolve. 




Ubuntu Server x64 18.04 running minimal xubuntu desktop


4.15.0-128-generic

Happens with wired and wireless mouse

Not a laptop  - no touchpad device

dpkg --reconfigure  did not help

---

### Post by HermanAB on 2020-12-28
# set mouse speed to default
xset m default

---

