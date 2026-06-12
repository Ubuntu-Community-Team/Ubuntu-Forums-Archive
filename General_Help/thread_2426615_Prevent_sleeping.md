---
title: "Prevent sleeping"
date: 2019-09-11
forum: General Help
---

### Post by Phil Binner on 2019-09-11
I have an Xubuntu desktop acting as my media machine.  It drives a TV through a Bose media centre, so I do not need the screen to shut down ever; I turn off the TV independently.  In fact it's a pain having it sleep, because then the bose can't find it and sometimes waking it up is very difficult.

I now have a further problem, because I'm about to have it playing music for a party, and I need it to go on independantly for several hours.

I have tried the Power Manager, but the most I can make it stay on for is 60 mins.  Even while it's playing music, if I don't touch the keyboard or mouse for an hour the sound and picture go off, even though VLC keeps on going.

I also did some research and found reference to an app called "inhibit", which sits in the tray. Unfortunately when I try to add it to the tray it's not available, and I don't know how to get it.

Can anybody help please.

---

### Post by dragonfly41 on 2019-09-11
Just as a problem solving exercise could you write a cron job to nudge the mouse every 15 minutes or so to keep sound and picture alive? You might use xdotool for this nudging.

---

### Post by speartip on 2019-09-11
Doesn't the program caffeine stop the screen from going to sleep?

---

### Post by HermanAB on 2019-09-11
When all else fails:
[https://www.aeronetworks.ca/2014/06/mouse-wiggler.html](https://www.aeronetworks.ca/2014/06/mouse-wiggler.html)

---

### Post by again? on 2019-09-12
Check your power manager setting.
When enabled uses dpms.
[ATTACH=CONFIG]284004[/ATTACH]

Can also check if dpms is enabled with...
```
xset -q
```

Try a startup script....
```
#!/bin/bash
sleep 10
xset -dpms
xset s off
```

Failing that, a simple loop script...
```
#!/bin/bash

while [ 1 ]; do
	sleep 60
	xdotool key shift	
done
exit 0
```

---

### Post by ajgreeny on 2019-09-12
My Xubuntu 18.04 on a desktop machine has an icon for an applet on the panel for the power-manager, part of Notification Area, which when right clicked shows a tick box for "Presentation Mode".

A tick in that keeps the machine running indefinitely.

---

