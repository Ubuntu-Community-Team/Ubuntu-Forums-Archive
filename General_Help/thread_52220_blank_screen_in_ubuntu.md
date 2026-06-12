---
title: "blank screen in ubuntu"
date: 2005-07-27
forum: General Help
---

### Post by wizo on 2005-07-27
hey guys, after i installed the nvidia drivers for my geforce2 Go 16mb graphics card, i rebooted the system, the screen shows me linux loading, and then i get a blank blank screen, as in, its not even on, when i ran some config thing in recovery mode, it says that my laptop screen couldnt be found, after that i reinstalled ubuntu again, any ideas or links that can help?? anyone experienced this problem and  wanna share hwo u solved it?  ](*,)  thx

---

### Post by Shiven on 2005-07-27
try editing your /etc/X11/xorg.conf and changing the Driver line from "nvidia" to "nv". if its already nv, nvidia should fix it, considering that nv and i have never got on...

if it all goes haywire again, switch it to vesa for guarenteed results, but it wont be using your card. if you run into any other problems please post them!

---

