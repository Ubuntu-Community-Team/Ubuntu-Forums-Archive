---
title: "What to do when window/display manager crashes?"
date: 2016-03-17
forum: General Help
---

### Post by lakeshore2985 on 2016-03-17
Every since I upgraded to Ubuntu 14.04.4 LTS (kernel 4.2.0-30), LightDM  keeps crashing all the time using Ubuntu's default video driver on my  NUC D54250XXX (Intel HD5000). The workarounds I found are either  shutting off "X" (Ctrl+F1 -> top [find Xorg's PID] -> sudo kill  <PID>) or restarting LightDM (Ctrl+F1 -> sudo restart lightdm),  but this won't let me continue with the existing session. Sometimes I  can lock the screen (Ctrl +Alt + L) and then log back in again without  having to lose my current session, but not always.

So is there a better way to handle the situation whenever LightDM crashes without having to lose the current session entirely?

---

