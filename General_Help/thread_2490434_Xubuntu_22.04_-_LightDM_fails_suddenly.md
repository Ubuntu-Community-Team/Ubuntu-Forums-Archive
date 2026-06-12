---
title: "Xubuntu 22.04 - LightDM fails suddenly"
date: 2023-09-04
forum: General Help
---

### Post by Petr_Be on 2023-09-04
Hello,

for no reason apparently (beside perhaps running apt upgrade) LightDM doesn't load the desktop in my Xubuntu 22.04 installation anymore.

The system starts normally (I can see the Xubuntu logo and I can make it switch to startup messages by pressing Esc - no errors there), but at the point when the desktop is supposed to start loading, the screen goes blank and after a while, the numlock LED on the keyboard starts blinking.

It's not possible to get to the virtual console using ctrl+alt+f4 (I tried many f's repeatedly, not just f4). I know other services are running, as it's possible to connect to Apache remotely. The only thing I can do at this point is press the power button to turn the computer off. The Xubuntu logo reappears for a few seconds before the shutdown.

I can get to the recovery mode, but I'm not sure what to do there. I tried apt update and apt upgrade, but there are no updates available (networking is enabled). I tried dpkg-reconfigure lightdm but that didn't help either. Do you have an idea what to do?

Thank you very much

bhy

---

### Post by Petr_Be on 2023-09-04
Update:

After checking lightdm.log, it seems the X server doesn't want to start. There are messages like: caught terminated signal, shutting down, stopping display manager, error connecting to X server. I also checked Xorg.log, but there are no errors (apparently the last messages are from the last successful X startup before this problem occurred.)

---

### Post by Petr_Be on 2023-09-04
Update:

after reinstalling lightdm, there is /var/log/lightdm/seat0-greeter.log which has many of these lines:

Failed to open PAM session: permission denied

So it's something related to PAM. How do I debug those? Thank you.

---

### Post by Petr_Be on 2023-09-04
Not sure what it was, but reinstalling lightdm-gtk-greeter solved the issue.

---

