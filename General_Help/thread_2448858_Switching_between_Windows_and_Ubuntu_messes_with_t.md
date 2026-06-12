---
title: "Switching between Windows and Ubuntu messes with the time on Windows."
date: 2020-08-15
forum: General Help
---

### Post by redflare on 2020-08-15
I have a dual boot setup with Windows 10 and Ubuntu.  If I switch from Windows to Ubuntu at 5:05PM and then switch back to Windows 10 hours later, Windows will still think that it's 5PM.  How do I fix this?  I only have this problem on Windows, I have to go to the time settings and press "sync time" to correct it everytime I log into Windows.

---

### Post by CatKiller on 2020-08-15
Windows assumes that the hardware clock is set to local time. Every other OS has that clock set to UTC. You can either tell Windows to use UTC for the hardware clock or tell Ubuntu to use local time for the hardware clock.

---

### Post by CelticWarrior on 2020-08-15
[https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

---

