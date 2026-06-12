---
title: "Help!"
date: 2008-05-11
forum: General Help
---

### Post by cheddah on 2008-05-11
Help! Recently tried hooking up external monitor to Dell 700m with Ubuntu Gutsy, and tried to adjust the resolution on the laptop after unplugging monitor because I could not view the bottom of my screen anymore. I made the resolution what it normally is, and rebooted. Now this screen flashes 3 times, and then goes nowhere.

Any help is greatly appreciated.

---

### Post by ibuclaw on 2008-05-11
1) Can you switch virtual terminals OK? Press "**Ctrl+Alt+F1**" through to "**Ctrl+Alt+F7"**".
Note for any changes.

2) Can you reboot into recovery mode?
If you can, issue this command when the shell opens:
```
dpkg-reconfigure xserver-xorg
```
Then type in "**exit**" to continue to Normal Boot.


Regards
Iain

---

### Post by cheddah on 2008-05-11
Oh God. Thank you so much!

Now the resolution is really low (like, 800x600 low). Is it safe to  just do System -> Preferences -> Screen Resolution?

Thanks again!

---

### Post by ibuclaw on 2008-05-11
Sorry for the late reply.

You've probably fixed it by now.

But, just for sake, the answer is "Yes, you can."

Although, check your restricted hardware first (In the "System>Administration" menu). Make sure all that should be enabled is enabled (ie: NVIDIA Graphics Drivers).

Once you've done that, reboot. And then try upping your screen resolution.

Regards
Iain

---

