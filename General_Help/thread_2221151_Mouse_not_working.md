---
title: "Mouse not working?"
date: 2014-04-30
forum: General Help
---

### Post by jack68 on 2014-04-30
Hi all, so I installed lubuntu 12.10 fresh and updated to 13.10. Very new to linux. Everything went ok except I started noticing the task bar at the bottom of the screen acting up (unable to click anything) can still navigate around with alt+tab. Desktop icons work some of the time. Can't seem to switch between tabs with the mouse on chomium and also clicking links on screen isn't working. ctrl+tab still works and searching through the page with tab still works, its the same story with the rest of the programs I use. Was playing around with task manager and stopping lxsession seems to get the taskbar working temporarily but other than that I have no clue where to start... Any bit of help would be seriously appreciated, thanks.

---

### Post by whitesmith on 2014-04-30
Welcome to the forum, **jack68**. Stopping daemons (services in Win-speak) is generally not a good idea unless you know exactly what they do. Try ```
xkill -a
``` to shut down the X-server (windowing system used in Ubuntu). This should be done from a tty (for example, Ctrl+Alt+F2) Restart the X-server by then entering```
xinit
```Get back with Ctrl+Alt+F7. Just restarting the machine might be easier. Cheers.

---

