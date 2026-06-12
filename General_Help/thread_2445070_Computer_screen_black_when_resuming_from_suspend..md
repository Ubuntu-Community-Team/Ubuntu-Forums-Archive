---
title: "Computer screen black when resuming from suspend."
date: 2020-06-08
forum: General Help
---

### Post by Bucky Ball on 2020-06-08
Hi all,

Using an MSI CX62 6QD laptop running Xubuntu-core 18.04LTS.

I upgraded this machine from 16.04 to 18.04 about a week ago and since then, when opening the laptop lid to wake it from sleep/suspend, the screen stays blank. No action. Have to hold down power button, restart machine.

I upgraded another laptop running Xubuntu-core from 16.04 to 18.04 at the same time and no such issues. I checked that machine and set the problematic one up the same way. Xscreensaver only (no Light-locker). Then again, I'm not sure the settings for Xscreensaver are the same because my machine, which is working fine, has no screensaver settings GUI installed (xscreensaver-settings I think) whereas the problematic machine does have a screensaver GUI installed.

Any further info required, just ask, and any ideas you might have, appreciated.

(PS: Maybe this should be in installations and upgrades, not sure, but I'll leave that to the mods to decide. :))

---

### Post by ActionParsnip on 2020-06-09
If you press CTRL + ALT + F1 to drop to CLI, does that work? If it does can you press CTRL + ALT + F7 to get the GUI back?

---

### Post by Bucky Ball on 2020-06-09
> If you press CTRL + ALT + F1 to drop to CLI, does that work? If it does can you press CTRL + ALT + F7 to get the GUI back? 

Yes and ... no. CTRL+Alt+F1 takes me to a CLI. CTRL+Alt+F7 takes me back to a blank, black screen. 

I logged into the CLI and tried issuing 'startx', a command I remembered from long ago, but that did nothing but take me back to a cursor, still in the CLI. 

If I issue 'sudo reboot -h now' from the CLI, reboot back to the blank screen, but now, CTRL_Alt+F1 does nothing. Still at black screen.

Hold down power button and start again.

Thanks for your input, AP. At least I know I can get to a CLI from there, so that's something.

---

### Post by Bucky Ball on 2020-06-10
* Bump *

Any help with this frustrating problem?

I will add that I did have the same issue when I installed 16.04 LTS onto this machine originally. Unfortunately, I can't remember what I did to fix that. The upgrade to 18.04 may have killed any custom tweaks I'd done and maybe those same tweaks would fix this same issue in 18.04.

---

