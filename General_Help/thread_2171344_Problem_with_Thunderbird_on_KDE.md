---
title: "Problem with Thunderbird on KDE"
date: 2013-08-30
forum: General Help
---

### Post by GreatBunzinni on 2013-08-30
After a recent system update, KDE ceased to be able to display Thunderbird's window.  Whenever I run thunderbird on KDE, the app appears to run well (it even checks out emails and addons such as firetray even display how many emails have been received) but the applicaiton window doesn't appear anywhere.

This problem doesn't manifest itself when I run Thunderbird on Unity, or Firefox in either desktop environment.

Does anyone have any idea on how to fix this problem?

---

### Post by GreatBunzinni on 2013-08-30
It appears I've solved this problem.  I had a custom window rule in KDE for Thunderbird, which forced any Thunderbird window to be included in any KDE activity currently opened.  

Unbeknownst to me, it appears this rule unleashed havoc on the latest KDE update. I don't know the reason for this behaviour, but deleting the custom window rule solved this problem.

---

