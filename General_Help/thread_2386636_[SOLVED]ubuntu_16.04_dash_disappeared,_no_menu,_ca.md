---
title: "[SOLVED]ubuntu 16.04 dash disappeared, no menu, can't move, resize, ect after update."
date: 2018-03-08
forum: General Help
---

### Post by roseruby on 2018-03-08
Hi after an update and turning off the computer then turning it on again after a few hours the dash has disappeared completely, I can't move or resize any windows ( the top menu bar is gone ) and using Ctrl + Alt + T is not opening the terminal but I can get into the terminal by right clicking the mouse.
Logging in as a guest is fine, everything there is normal.

Googling online for solutions all day but nothings worked so far.

Things I have tried so far:

Checked the appearance and settings, tried Restore Behavior Settings.

Tried updating and Installed CompizConfig and enabled the unity plugin.

Checked the windows decoration on effects.

Used unity --reset to reset unity.

Tried various guides to restore it in previous Ubuntu's like rm -rf .compiz-1, rm -rf ~/.config.
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo service lightdm stop
rm ~/.config/dconf/user
sudo service lightdm start

P.S still quite an inexperienced user here.

---

### Post by burnsmicro2 on 2018-03-09
Another similar post.

[https://ubuntuforums.org/showthread.php?t=2386528](https://ubuntuforums.org/showthread.php?t=2386528)

---

### Post by roseruby on 2018-03-11
Ok thanks, guess I'll head over to that thread. (Edit) Problem solved! For anyone else having the same problem clearing the cache did the trick. :)

---

