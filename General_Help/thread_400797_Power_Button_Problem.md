---
title: "Power Button Problem"
date: 2007-04-03
forum: General Help
---

### Post by MrGrey1 on 2007-04-03
Hi All,
I have a 6.1 power button issue.
I used to click on the red power button on the task bar and a window would open with the power off options enabling me to select shutdown. This enabled me to turn the computer off without having to log out.
Now, for some unknown reason, when I hit the red power off button it logs me out and switches to the login screen and I then have to select shut down from the Options menu at the bottom right of the screen. As I VNC into this machine from the other side of the house and usually turn it off from there this really sux. My only option to shutdown remotely is to use the command line to sudo halt.
I've searched every option in the GUI that I can find and have been trawling the forums for 2 days without any luck. I'm sure it's probably something really obvious but it seems to be eluding me. Any help would be greatly appreciated.

---

### Post by MrGrey1 on 2007-04-13
Issue seems to have resolved itself... had given up on it and was messing around setting up ssh and all of a sudden the shutdown screen appeared when I went for a reboot... got me stumped. There's a chance it's PEBKAC but I'm pretty certain it ain't.

---

### Post by zvacet on 2007-04-13
It is update related.I expirienced same thing as you do ,but with another updates everything is back in place.

---

### Post by MrGrey1 on 2007-04-13
SurR3al pointed me to the setting that affects this option. I new it was something simple I was overlooking...

SurR3al
"i went to 'system -> preferences -> sessions' and checked 'ask on logout'
after that everything was normal"

:D

---

