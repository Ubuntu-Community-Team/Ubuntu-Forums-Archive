---
title: "suspend not working.."
date: 2019-10-26
forum: General Help
---

### Post by Furycd001 on 2019-10-26
HI.. Running a fully up-to-date xubuntu 18.04.3 & suspend has suddenly stopped working. I have been using the script below for a while now and it has always worked. As of today every time I run the script the screen just locks and the system doesn't suspend. I haven't made any changes to my system other than installing updates. If I open up a terminal and manually execute **systemctl suspend **or **xfce4-session-logout --suspend** the same thing happens. The screen just locks and the system doesn't suspend. Someone help me please because I need to be able to suspend my laptop....


```

#!/bin/bash

# Set how dim we want the screen to go (percentage, out of 100)
dim=4

# Pack up your toys
previous_dimness=$(xbacklight -get)

# Turn down the lights
xbacklight -set $dim

# Lock the door (this requires a password to get back in)
xflock4

# And go to sleep
xfce4-session-logout --suspend

# When we wake up, turn the lights back on
xbacklight -set $previous_dimness

```

---

### Post by Furycd001 on 2019-10-28
Anyone able to help me with this problem :?

---

### Post by ajgreeny on 2019-10-28
That seems a rather complicated way to get the suspend working in locked mode.

The security tab of ***xfce4-power-settings-manager*** already has an option to lock the screen when entering suspend, so if you just enable that you can either use the ***xfce4-session-logout --suspend*** command in a script, or more simply, do what I do and use suspend (with lock) on closing the laptop lid (from xfce4-power-settings-manager), or use a keyboard shortcut to ***xfce4-session-logout --suspend*** linked to the Pause/Break key, which I use a lot on my desktop machine.

---

### Post by Furycd001 on 2019-10-28
Thanks for the reply and for the heads up. A good while ago I started using that script because I can across a big that was preventing suspend from working correctly on my laptop. There was something open on launchpad about it, but I can't find the link. Maybe it's fixed by now so I'll set a new keybinding and stop using the script....

---

