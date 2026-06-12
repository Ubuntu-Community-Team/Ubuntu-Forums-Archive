---
title: "plugin container pushes cpu % to above 70 or 80"
date: 2012-11-07
forum: General Help
---

### Post by Ohzed on 2012-11-07
when using firefox 16, a lot of times it's flash plugin-container child process hogs cpu power and raises it's percentage to numbers above 70 or 80 (as I see when using the program "top" in the terminal) even when no firefox tab i have open is using flash player, I'm using the latest version of flash, via 11.10's update manager, and the fan (i'm assuming) is noticeably louder for long periods of time. There's no performance problems that i notice, but it's very annoying and i feel this is being really hard on my laptop and overstressing and overheating it. Is anyone else having this or have had this problem before, and does anyone know why this could be happening and how to fix it?

---

### Post by mardybear on 2012-11-07
Hi Ohzed...

It's easy to disable.

Enter about:config as a URL on your Firefox browser.

Use the search to find dom.ipc.plugins.enabled.

Double click on it to change true to false.

Might have to restart Firefox.

mardybear

---

### Post by Ohzed on 2012-11-08
well I still want Flash enabled, like for when I watch videos that require Flash, but even if I only turned it on when needed, it'll probably still try to max out the cpu.

---

### Post by mardybear on 2012-11-08
Hi Ohzed...

The about:config tweak i suggested just disabled plugin-container, NOT flash. Go ahead and try it, it can easily be reversed. It should take care of your plugin-container issue.

mardybear

---

### Post by pqwoerituytrueiwoq on 2012-11-08
use one or more of the following addons
adblock+
noscript
flashblock

---

