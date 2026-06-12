---
title: "keyboard probs"
date: 2007-02-28
forum: General Help
---

### Post by celticbhoy on 2007-02-28
Hi new to linux and ubuntu, having a prblem setting up the keyboard layout under the settings-->prefrences option. When I try to make a change the following error comes up. It also happens when I try to set up a use for the windows key using gconf-editor.

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

any help to resolve this would be appreciated.

---

### Post by drewk1 on 2007-03-23
I'm having the same problem.

I'll see if I can find a solution and post here.

---

