---
title: "Ctrl + Shift keys not not working"
date: 2023-01-25
forum: General Help
---

### Post by elliotfklein on 2023-01-25
Hello! I've got a Dell Inspiron 5505 running Ubuntu 22.04 (GNOME + X11), and all four of my left Ctrl, right Ctrl, left Shift, and right Shift keys are not working — pressing them doesn't register in `xev`, the keyboard layout GUI, or (apparently) the hardware (keyboard backlight doesn't activate when I press them)

For a while, only the Ctrl key was fritzy: it would occasionally work, or I could fix it with `setxkbmap` and turning on "Pointer Location" (highlight pointer on Ctrl press) in GNOME Tweaks (I still don't know why this worked).

Now, the Shift key still occasionally works, but most of the time none of my Ctrl or Shift keys work.

All the keys on my external USB keyboard work fine, I'm just getting tired of carrying it everywhere :D

Using GNOME Tweaks "Ctrl position", I can remap my left Ctrl to left Caps Lock, which works. (I have "Show Extended Input Sources" on in GNOME Tweaks, but that shouldn't make a difference)

My keyboard layout in Settings is correct (English, US), and there's only that one "Input Source" listed.

I've confirmed that my laptop keyboard doesn't have Fn Lock or anything turned on (but that shouldn't matter). I also tried reinstalling X11 and upgrading from 20.04 to 22.04 (no changes, the issue is still the same).

All of these signs (USB keyboard, still working sometimes, being very frequently used keys) would seem to point to it being a hardware issue, but I can't think of why this would affect the right Ctrl/Shift keys in addition to the left (since I almost never use the right keys).

I checked this forum and a few others (that's where I originally found the `setxkbmap` and GNOME Tweaks workaround), but haven't found anything that fully fixed it.

Would appreciate any ideas for diagnosing or fixing this, please let me know if there's any other info I can provide that'd be helpful here. Thanks!

---

### Post by Impavidus on 2023-01-26
It really looks like a hardware issue.

---

