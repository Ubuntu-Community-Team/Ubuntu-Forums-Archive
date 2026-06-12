---
title: "Problem with Workspace Switcher in Ubuntu 12.10"
date: 2012-10-25
forum: General Help
---

### Post by KevinRandolph on 2012-10-25
Hi,

I'm having a small problem with the Workspace Switcher in Ubuntu 12.10.

I reconfigured it to by 1x6, but after every reboot it reverts to the default 2x2.

This works correctly with the Beta version.

I'm running up-to-date Ubuntu 12.10 (32-bit) with Gnome desktop (not Unity) under VirtualBox under Windows 7.

Such a small problem for an outstanding piece of work that is Ubuntu.  You guys and gals do an outstanding job.  Thanks.

KR

---

### Post by mc4man on 2012-10-25
Should be working ok now, there was an issue previously that was fixed right before or after release.
When you say "Gnome desktop" do you mean Classic or Classic (No effects)

The former uses compiz & the setting should be made in ccsm > General Options > Desktop size

The later uses metacity & can be set thru the WS switcher preferences & or in dconf-editor, path & key -  
org.gnome.desktop.wm.preferences num-workspaces

---

### Post by KevinRandolph on 2012-10-25
Thanks mc4man.

Yes, your are correct in that I'm using Gnome classic.

Based on your post, I am going to try Classic (no effects) and see if that works better.  I had a problem with compiz crashing.

Thanks for the pointers to the configuration utility for Workspace Switcher for Classic and Classic (no effects).  I appreciate the help.

KR

---

### Post by KevinRandolph on 2012-10-25
Update:

Switching to Classic (no effects) did the trick.  And I checked the the Beta 12.10 VM and it is also configured to use Classic (no effects).

Thanks again for the tip.

---

### Post by mc4man on 2012-10-25
It appears the Classic (compiz) session can still have some very inconsistent behavior. 
If going back to it at some point I'd leave the WS switcher pref's at the default of 1 & 1 & just set in ccsm as mentioned before.
But in any event Classic (compiz) seems liable to go south at any point

(I just logged into it on a test user where it was ok before & it somehow decided to enable the unity plugin... & go back to 2x2
Classic (compiz) remains a bit of a mess

---

