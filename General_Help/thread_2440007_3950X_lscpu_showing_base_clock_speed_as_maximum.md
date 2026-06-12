---
title: "3950X lscpu showing base clock speed as maximum"
date: 2020-04-04
forum: General Help
---

### Post by mrpistolero on 2020-04-04
I'm currently using the 20.04 beta, I'm just trying to find a way to get this fixed and I'm not finding anything anywhere at all. My 3950X, according to lscpu, is running at 2.2Ghz which is well below the base clock speed of 3.5GHz. [ATTACH=CONFIG]285395[/ATTACH]

---

### Post by CelticWarrior on 2020-04-04
Welcome.

Please read the entry about "max CPU". If such speed isn't required the CPU will throttle back to what it really needs thus saving energy.

---

### Post by mrpistolero on 2020-04-04
So that's the case even though it's being reported that base clock is max clock??

<edit>recorded a video using Cheese, monitoring clock speed in terminal using watch -n1 "lscpu | grep 'MHz' | awk '{print $1}'" ..ran the said video through handbrake and it's still boosting to approximately the same clock speeds I'm getting in Windows. </edit>

---

