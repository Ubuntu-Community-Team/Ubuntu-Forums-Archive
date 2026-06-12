---
title: "FireFTP extension crashes Firefox"
date: 2006-12-05
forum: General Help
---

### Post by oliwally on 2006-12-05
I've just started having a strange problem since upgrading to Firefox 2 and the FireFTP version 0.94.4 extension. When opening FireFTP, Firefox crashes.

More detail:
When I click to open FireFTP two tabs open, one with FireFTP, the other with a FireFTP donation website, the latter of which is displayed. When I close the donation tab, Firefox crashes. The same happens when I leave the donation tab open and click on the FireFTP tab.
I've tried reinstalling FireFTP several times and mucked around with different options, but to no avail. I don't have this same problem in WinXP (same browser, same extension).

Any ideas anyone?

---

### Post by yopnono on 2006-12-05
Latest FireFTP is 94.6 try that one.
Also clear out all traces of it from pref.js in the firefox profile

---

### Post by oliwally on 2006-12-05
> **yopnono said:**
> Latest FireFTP is 94.6 try that one.
Also clear out all traces of it from pref.js in the firefox profile

Thanks so much for helping out. I've tried your suggestion and have had the same result - firefox crashes.

---

### Post by yopnono on 2006-12-05
Disable all addons, and try with only fireftp enabled.
Or create a new profile and install only fireftp and try. If that works then add ext after ext and see which will cause the crash

Trial and error

---

### Post by oliwally on 2006-12-07
> **yopnono said:**
> Disable all addons, and try with only fireftp enabled.
Or create a new profile and install only fireftp and try. If that works then add ext after ext and see which will cause the crash

Trial and error

Hmm, strange indeed.

I've set up a second profile and duplicated the extension setup. This worked well without probs.

I uninstalled all the extensions from my non-working profile and re-installed  fireftp - still no luck. I even went to the prefs.js and deleted anything that looked like it had something to do with any of the extensions - no success.

In the end I deleted the whole prefs.js of my non-working profile (firefox creates a new one when it first starts) and this, finally !!, worked well, although I have to reinstall the themes and extensions. No big deal though.

Thanks so much for your suggestions yopnono, they gave me a starting point (the prefs.js file) and led me down the path of success with this issue.


EDIT - It appears that the Noia 2.0 (extreme) v.3.34 is to blame for my problems. Enabling it makes fireftp crash firefox (although it seems to be fine in WinXP)

---

