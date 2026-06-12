---
title: "Power management and screensaver"
date: 2008-04-28
forum: General Help
---

### Post by Bachstudies on 2008-04-28
I have noticed that power management doesn't seem to work automatically in Hardy on either AC or battery. I can use xset to manually force the screen off and manually use suspend and hibernate so I know my Dell Inspiron 1501 is compatible. I have also tried letting the screensaver start automatically and strangely the screen fades to black but immediately returns. I am convinced that the laptop never manages to count enough idle time to invoke monitor standby and suspend if it is reliant on a screensaver countdown. If someone can help figure out why the screensaver never gets past the fading part, I think the rest will start working again.

---

### Post by matthias_k on 2008-04-29
Hmm, I only observed my screensaver activating once, but it seemed to work properly. But I can confirm that power management is broken for my laptop model (Samsung R55), as it does not react on "laptop lid closed" events to trigger suspension, screen locking and so on.

---

### Post by Bachstudies on 2008-05-01
Unless I am mistaken, there have been no updates to Hardy since official release day (at least for the default packages included in the installation). However, my power management has started working by itself. Only thing now is that when ubuntu automatically suspends my laptop after a certain amount of time, i do not need to enter a password on restarting. Password is needed when i manually click 'suspend'.

---

