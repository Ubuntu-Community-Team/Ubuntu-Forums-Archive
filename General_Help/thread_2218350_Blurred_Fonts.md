---
title: "Blurred Fonts"
date: 2014-04-20
forum: General Help
---

### Post by ebutts531 on 2014-04-20
Something is wrong with my nvidia driver or xorg settings. Fonts on my computer become blurred. When I move the whole window of a appliction or nautilus fonts redraw fine, but when I move my cursor or interact inside the window fonts will become blurred and unfocused. Tried restarting lightdm, with no fix. I installed another version of the nvidia driver and restarted which seemed to fix the problem, but after another restart, I return to the same issue. Something is happening right after a newly installed driver, but will not remain constant for subsequent restarts and shutdowns.

Any help or ideas would be greatly appreciated. I did not see any similar reports on the web, so I think the problem may be related to my config.

---

### Post by ag4032 on 2014-09-26
Any solutions to this problem?

---

### Post by ag4032 on 2014-09-26
I've identified the problem: "Enable FXAA" should be deactivated in the nvidia-settings. This option and compiz conflict with each other for some reason.

---

