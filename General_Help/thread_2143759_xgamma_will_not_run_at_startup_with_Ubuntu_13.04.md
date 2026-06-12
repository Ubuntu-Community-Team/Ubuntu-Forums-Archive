---
title: "xgamma will not run at startup with Ubuntu 13.04"
date: 2013-05-10
forum: General Help
---

### Post by superglide03 on 2013-05-10
The command I'm using in Startup Applications launcher is     sleep 90 && xgamma -gamma 0.7   I was trying this because     xgamma -gamma 0.7   did set gamma at startup but it was reset within seconds.  This set and reset happened while I was still on the logon screen.   This command (sleep 90 && xgamma -gamma 0.7) does work in the terminal, I just don't know how to make it work in the startup launcher.  Thank you anybody that takes the time to help me with this.

---

### Post by CatKiller on 2013-05-10
I don't think having a sleep command in the startup applications has ever worked. You can make a shell script that has the two commands and put that in your startup applications though.

---

### Post by superglide03 on 2013-05-12
Thank you Cat Killer.  Learned another way to affect startup and a bit about scripts. Worked perfectly.

---

