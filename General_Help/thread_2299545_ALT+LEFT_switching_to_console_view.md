---
title: "ALT+LEFT switching to console view?"
date: 2015-10-19
forum: General Help
---

### Post by kawazu on 2015-10-19
Folks;

experiencing a *rather* strange error: Running 15.10 pre-release builds on my notebook, I fail to use the usual (ALT + cursor-left) key binding to go back in Firefox browser history. Right now, using this keybinding (same as using ALT+F4) will immediately bring me to some no-X VT, the same I managed to reach ever since on Linux using CTRL+ALT+F<n>. This is pretty confusing and annoying - is there any way to change this behaviour?

TIA and all the best,
Kristian

---

### Post by kawazu on 2015-10-20
Strange enough, this seems to happen only (a) when running multiple monitors and (b) at some point in time. Started up my machine this morning - everything fine. Rebooted now - everything fine. In between however, at some point this behaviour starts to appear and I have no clue why. Any log files that could be helpful here?

---

### Post by kived on 2015-10-20
Same thing happening to me. I always use two monitors, and I use Terminator a LOT. One of the biggest advantages to Terminator is the ability to easily switch between the split panes using ALT-Left/Right/Up/Down. Also sucks for PyCharm, using ALT-Left/Right to go back and forward to other edit locations. Reboot does seem to fix it sometimes, but it always comes back.

---

### Post by kived on 2015-10-20
I filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1508211](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1508211)

Please see if there is any information you can add. Specifically, I am running Ubuntu GNOME, and apparently I'm using Wayland. Please comment on the bug if this is the case for you as well, or if you are using a different X server and also have this issue.

---

