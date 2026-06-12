---
title: "Getting PulseAudio To Start on Boot"
date: 2013-04-26
forum: General Help
---

### Post by Simeo on 2013-04-26
I know it must be something simple but for some reason my pulseaudio does not start on boot. I always need to a wait a couple moments, press alt+F2, and type/select "pulseaudio" in the command box to start it up. After that it works without a problem.

How would I make it automatically start on boot? Running Ubuntu 13.04 

Thank you.

---

### Post by ajgreeny on 2013-04-26
It should start when you login, but check that **start-pulseaudio-x11** is in your startup applications list, and if not add it.

That is what starts it in my Xubuntu 12.04, so is a good place to begin.

---

