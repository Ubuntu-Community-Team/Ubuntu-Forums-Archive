---
title: "Disable system-wide keyboard shortcuts?"
date: 2017-06-06
forum: General Help
---

### Post by The Bright Side on 2017-06-06
Hey guys! I'm trying to play Commander Keen in DOSBox and whenever I hit Ctrl+Alt+4 or 6 on the numpad (which is common in the game), the DOSBox window jumps around my screen.

I looked in the "Keyboard" settings to see whether I could disable this shortcut, but no dice.

Any config file I could edit?

---

### Post by vanadium on 2017-06-06
This may help: [https://www.gog.com/forum/general_archive/how_to_disable_all_dosbox_internal_shortcuts](https://www.gog.com/forum/general_archive/how_to_disable_all_dosbox_internal_shortcuts)

---

### Post by The Bright Side on 2017-06-07
Hey vanadium, thanks for digging this one up! It didn't help me fix Ubuntu's interfering system-wide hotkeys, but I came up with a workaround.

When I run DOSBox in full screen, there's no interference with the keys. The problem is that sound over HDMI stops working in full screen. So I ended up running a separate audio cable from my PC's line out to my home theater receiver. That way, I have full screen, sound and no problems with interfering system hotkeys.

Thanks again!

---

### Post by vanadium on 2017-06-08
Glad you could find an acceptable solution. If you are using stock Ubuntu, and you want to disable specifically  Ctrl+Alt+4 or 6, then you can do so in Compiz Config Settings manager. You eventually need to install that as it is not installed by default. I think you will find the hotkey assignments in the "Grid" plugin. You would need to disable them there. On a more advanced level, I guess one could create a script to start dosbox, where these keys are temporarily switched off with a script (it is a dconf setting), and be turned back on on exit.

---

