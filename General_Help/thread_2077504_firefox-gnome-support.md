---
title: "firefox-gnome-support"
date: 2012-10-28
forum: General Help
---

### Post by james_mcl on 2012-10-28
I'm not entirely sure what this package does - Synaptic didn't provide much information:

"allow(s) Firefox to take advantage of technologies such as GConf, GIO libnotify"

and I'm thinking about uninstalling it. Partly this is because I don't use gconf-editor or any of its successors to configure Firefox, and partly because files I download in Firefox are being added to the "Recent Documents" list and pushing my *actual* recent documents out - and I suspect this package is responsible.

Has anyone on these forums ever tried uninstalling this but keeping Firefox on Gnome or Mate? How did it work for you?

---

### Post by mardybear on 2012-10-28
Hi james_mcl.

I use Ubuntu 10.04 and the latest Firefox 16. My Firefox has an add-on extension called 'Ubuntu Firefox Modifications'.

This may be different than your firefox-gnome-support or maybe similar. When in Firefox add-ons i don't have the option to remove, just disable 'Ubuntu Firefox Modifications'. This appears to have no ill effect on system performance and i'm hoping it just helps the system run leaner.

If you have the option to disable, just try disabling it first and see if your system still runs okay or if you notice any adverse problems.

mardybear

---

### Post by james_mcl on 2012-11-22
Apologies for delay in replying - I've found out what was causing the Recent Documents problem, and it wasn't firefox-gnome-support or xul-ext-ubufox. I thought I'd better post an explanation here for anyone with the same problem.

There's a preference in about:config which I had set to false, expecting it to prevent downloads from being added to Recent Documents:

browser.download.manager.addToRecentDocs

Actually, this preference only affects Windows installs of Firefox, but when someone set it to false and found that this had no effect, they filed a bug report ([https://bugzilla.mozilla.org/show_bug.cgi?id=646351](https://bugzilla.mozilla.org/show_bug.cgi?id=646351)). One of the Firefox devs explained that setting this preference to false stopped FF making a call to the underlying OS to add the saved file to Recent Documents.

HOWEVER, the dev went on to explain, if, like me, you've set Firefox to "Always ask me where to save", Firefox calls up the operating system's file-location-chooser-thingy. And when you save the file, it's this that makes the call to add it to Recent Documents, not Firefox.

It's not clear if this can be fixed without breaking the Recent Documents list for other applications - on Windows systems, a parameter can be used to prevent saved files being added to Recent Documents, but the Firefox developers really didn't seem very interested in implementing this fix. Anyway, there may not be such a parameter in any of Gnome/MATE/Unity/KDE/XFCE/LXDE etc, and without modifying the FF source there'd be no way to get Firefox to make use of it anyway.

---

