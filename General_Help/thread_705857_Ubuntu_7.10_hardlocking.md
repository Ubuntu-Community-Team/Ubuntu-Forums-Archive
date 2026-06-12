---
title: "Ubuntu 7.10 hardlocking"
date: 2008-02-23
forum: General Help
---

### Post by Holman on 2008-02-23
I have been experiencing some pretty random freezes and any help would be appreciated. My computer is freezing anywhere from every couple minutes to every day.

During these freezes the mouse and keyboard become completely unresponsive (CTRL + ALT + BACKSPACE doesn't even work). These freezes last until I physically restart it. I have left it frozen for upwards of a day and it has never unfrozen. There don't seem to be any errors in the logs at the times of the freezes.

If I am on one of the full screen terminals running processes from my normal screen it will never freeze, leading me to believe it is something graphical either with compiz or the graphics driver. Before I installed my second monitor and switched to the restricted driver (nv) it never froze.

---

### Post by CRCarl on 2008-02-24
One of the things I do when I am trying to diagnose hardlocks is to pipe /var/log/messages to a file I can look at after I reboot. 

```
tail -f /var/log/messages > messages.txt &
``` in the console.

Also you can try and upgrade the restricted drivers. Do this by going to "System -> Restricted Drivers Manager" Uncheck the nvidia driver, click Disable. Then without rebooting re-enable the nvidia drivers, then reboot. 

Good luck.

---

