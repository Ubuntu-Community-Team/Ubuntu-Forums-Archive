---
title: "Display screen goes blank"
date: 2016-12-01
forum: General Help
---

### Post by loungehake on 2016-12-01
I run Ubuntu 16.04 LTS 64-bit.  After a short time of inactivity the display goes blank and the system is apparently unresponsive.  The power settings for 'Suspend when inactive' are set to 'Don't suspend'.

The only way to get things running again is to power off or reset the PC.

Does anyone else experience this behaviour? I cannot recollect this with Ubuntu 14.04 LTS 32-bit.

---

### Post by kingneutron on 2016-12-01
--What hardware do you have?  What happens if you hit Ctrl+Alt+F1?

--Try running attached script (it turns off screen blanking in X, but does not affect the "xscreensaver" daemon) and let me know if it helps, could be screensaver settings - but that should not hang the system. Possibly video driver? Please Post results of ' lspci ' so we have a little more to work with...

```

#!/bin/bash

setterm -blank 0 -powerdown 0 -powersave off
xset s off dpms 0 0 0
xset s noblank 

```

---

### Post by ajgreeny on 2016-12-01
Go to System Settings ->Brightness and Lock and disable the locking completely; that should do it I think.

---

