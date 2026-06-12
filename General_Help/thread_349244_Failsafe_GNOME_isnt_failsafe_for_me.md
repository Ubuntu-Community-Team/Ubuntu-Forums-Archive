---
title: "Failsafe GNOME isnt failsafe for me"
date: 2007-01-29
forum: General Help
---

### Post by ss0007 on 2007-01-29
Hi ,

 I trying to prevent Beryl loading up from startup programs .Because of my driver issues , GNOME reverts back to login screen evry time I log-in. So , I tried GNOME fail-safe mode , but unfortunately , Beryl tries to load again and reverts me back to login screen as before.
Even as notification comes ,saying the Startup items are being skipped.

Is there any way thru console ,that I can remove the startup items I have added in Sessions ? 

Thanks in advance ,

---

### Post by jornahow on 2007-01-30
I had precisely the same problem.  i was running an nvidia proprietary driver.  I solved the problem by booting in failsafe (recovery) mode to terminal, then invoking startx.  I removed beryl entirely and was then able to login normally, but any application that used xgl (such as my screensaver) crashed me back to the login screen .  I followed the advice to reinstall my Nvidia graphics driver and this solved the problem.  I used a newer 9762 beta driver - seems to work well.  I then installed Beryl from synaptic and everything works again.  I hope this will help.

jornahow

---

### Post by ss0007 on 2007-01-30
Thx friend , finally I could see my lovely GNOME back to life ...

---

