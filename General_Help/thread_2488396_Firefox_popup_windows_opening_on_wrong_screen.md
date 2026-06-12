---
title: "Firefox popup windows opening on wrong screen"
date: 2023-07-04
forum: General Help
---

### Post by troffasky on 2023-07-04
Using KDE on 23.04.
By 'wrong screen' I mean, not the screen where my mouse cursor is ['Active screen follows mouse'], which is also not the monitor I have in Display Configuration as 'Primary'.
This happens with my actual Firefox profile and a new one I just created for testing. I cannot see anything in about:preferences regarding screens, so for these two reasons, I don't think this is a Firefox issue. But I've also tried Openbox, with the same behaviour, so it seems like it's not Kwin, either!
If I create a new window with Ctrl+N, it appears on the current screen, it only seems to be site-generated popups that do this.
There are some Firefox help suggestions like, "open the popup, move it to the correct screen, close Firefox, then the next time it opens, it will be on the correct screen" which I have tried but it does not work. 

Any ideas?

---

### Post by troffasky on 2023-07-12
Tried using a window rule in kwin to move the window to a different screen, but all that happens when I run the rule is that the titlebar flickers.

---

### Post by troffasky on 2023-07-12
This is infuriating, the only rule action that works is "Force" changing the screen. If I "Apply Initially", nothing happens. Unfortunately Force then means I cannot manually place a Firefox window on the "wrong" screen.

---

