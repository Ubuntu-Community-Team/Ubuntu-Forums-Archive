---
title: "[Lubuntu] CPU running at 100%"
date: 2013-03-09
forum: General Help
---

### Post by Kols on 2013-03-09
Hi! 

For some reason, my single core processor is now constantly running at 100%. As you can see in the screenshot of htop, the process /usr/bin/lxsession -s Lubuntu -e LXDE is taking up most of the processor's power. Obviously, I can't kill it, but what else should I be looking for?

I'm running Lubuntu 12.10 32-bit on an old laptop. OS normally use approx 2% CPU at idle.

Cheers!

---

### Post by Kols on 2013-03-09
Hi! 

For some reason, my single core processor is now constantly running at 100%. As you can see in the screenshot of htop, the process /usr/bin/lxsession -s Lubuntu -e LXDE is taking up most of the processor's power. Obviously, I can't kill it, but what else should I be looking for?

I'm running Lubuntu 12.10 32-bit on an old laptop. OS normally use approx 2% CPU at idle.

Cheers!

---

### Post by varunendra on 2013-03-09
Threads merged.

Please do not post multiple threads for same question.

---

### Post by Kols on 2013-03-09
Okay, so I actually fixed the problem.

I'm using compton as composite manager and guake as terminal. Sometimes, guake loads too early in the startup process, and real transparency isn't loaded. Therefore, I made a script, called guake-autostart.sh. I call it from /etc/xdg/lxsession/Lubuntu/autostart by adding the line

@sh /etc/xdg/lxsession/Lubuntu/autostart-guake.sh

which is the reason my box is going crazy, trying to start a script that doesn't excist. Solution is therefore to change that line in /autostart with the correct filename....

Sorry for taking up your time, guys, I'll be leaving now...=P

---

