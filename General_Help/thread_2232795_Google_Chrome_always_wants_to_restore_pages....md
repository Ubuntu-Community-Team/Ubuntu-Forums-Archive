---
title: "Google Chrome always wants to restore pages..."
date: 2014-07-04
forum: General Help
---

### Post by Dr. McKay on 2014-07-04
I'm running Ubuntu 14.04, using Google Chrome as my main browser.
Every time I boot up my machine, Chrome wants to restore tabs, even though I closed the browser normally before turning off my machine.
It only does this once, after a boot or reboot. When I close the browser en reopen it during the same session, there's no problem.

Is this a bug ?

---

### Post by slickymaster on 2014-07-04
Try to reset the browser settings first:
[LIST]
[*]Click the Chrome menu on the browser toolbar.
[*]Select Settings.
[*]Click Show advanced settings and find the "Reset browser settings” section.
[*]Click Reset browser settings.
[/LIST]

If that doesn't work, try renaming your **/home/username/.cache/google-chrome/Default/ **folder to something else like "Default_Old" and then restart Chrome and let the folder get re-created automatically for you.

---

### Post by bachsteinsk on 2014-08-08
Same problem here for Chromium. Renaming the Default folder and then resetting the browser settings worked for me -- thanks slickymaster.

---

### Post by sportsdude81 on 2014-10-09
Just moving the Cache folder and restarting Chrome worked for me.  No need to reset settings in my case.

Edit: only worked one time after that in continued to have to have the same issues.

---

### Post by TrueFact on 2015-05-28
Chrome never actually close when you close all its windows. Thus, when you are rebooting, Ubuntu will kill the background apps, and this when chrome thinks it crashed and proposes to restore your session when you run it again.

If you don't want background apps, you can disable this option as described [here]("https://support.google.com/chrome/answer/1184722?hl=en").

---

### Post by diego-giglio on 2015-12-17
Rename /home/user/.cache/google-chrome/Default to Default.old resolved to me. Now, my chrome works fine :p
Thank you very much

---

