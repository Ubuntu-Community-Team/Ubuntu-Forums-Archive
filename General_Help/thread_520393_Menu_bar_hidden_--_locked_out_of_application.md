---
title: "Menu bar hidden -- locked out of application"
date: 2007-08-08
forum: General Help
---

### Post by lodp on 2007-08-08
It seems I accidentally hid the menu bar in the digikam application, now I can't figure out how to put it back in place. I've had the problem in other applications, and frequently pushing CTRL+M would help. But here it doesn't.

Trying to fix this, I right-clicked the toolbar (which didn't reveal an option to un-hide the menu bar) and out of curiosity clicked on "hide toolbar". Now the toolbar is gone too, and I can't get that back either (since I can't get into the appropriate menu anymore). W-T-F?

Is there some keybord shortcut to get the menu bar back?

This is super annoying. And I've witnessed it in quite a number of applications in Kubuntu. You accidentally hit a key or a menu option and bang there you are without a menu bar.

**EDIT:** Got rid of this by removing the digikam config file: ~/.kde/share/config/digikamrc
this creates a new config file with the menu bar back in place. you might be able to achieve the same thing by editing the file. the whole thing is probably related to this bug: [http://bugs.kde.org/show_bug.cgi?id=147771](http://bugs.kde.org/show_bug.cgi?id=147771)

---

