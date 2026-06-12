---
title: "kernel update available on one computer, but not on the other"
date: 2015-12-17
forum: General Help
---

### Post by jaarvidsen on 2015-12-17
hi
 im running ubuntu gnome 15.10 64 bit on 2 computers, one gaming desktop(dual boot with win 7) and one ultrabook. both are set up exactly hte same way with the same repos and both using the same mirrors, its identical. the only real difference between the 2 is that the desktop has nvidia proprietary drivers installed and that the desktop is an AMD and the ultrabook intel

anyway today the ultrabook updated to kernel 4.2.0-21 but the desktop is stuck on 4.2.0-18. it doesent matter how many times i run hte software updater it just wont find the newer kernels on the desktop machine. as i said repos/mirrors and all settings in software & updates are identical

any help?

---

### Post by deadflowr on 2015-12-17
It's called [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").

The basics of it is that in order to keep regressions hitting systems to the minimum, the updates get rolled out slowly to a few users first, then if the margin of errors is low enough it gets rolled out to more.
And so on, until all users are updated.

This only affects the Software Updater way, it does not apply to running the apt-get update/upgrade commands through the terminal.
(or at least it shouldn't affect the terminal way...)

---

### Post by jaarvidsen on 2015-12-17
thanks
hmm ive never not gotten security updates instantly before..

edit: sudo apt-get update/upgrade - still not showing up

---

