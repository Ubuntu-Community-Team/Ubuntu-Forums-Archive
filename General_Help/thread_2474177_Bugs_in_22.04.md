---
title: "Bugs in 22.04"
date: 2022-04-23
forum: General Help
---

### Post by palteater on 2022-04-23
Instead of filing bug reports and watch them vanish into cyberspace, I figure I'd list the various errors I have so far encountered after one day with 22.04. Feel free to ignore them.

PC1 = fresh install, PC2 = do-release-upgrade from 21.10

OpenVPN b0rks. Network-manager seems to mull over it for a bit, then drops. Using nmcli I see that it does in fact connect for a minute, then disconnects. Worse: even though it claims to be disconnected, whaismyip.com confirms that the VPN tunnel does in fact work?!?
PC2 using the same old OpenVPN settings - no trouble. Works as it used to on both.

Related: sometimes when I click on the VPN settings on PC1, the setting window freezes and eventually crashes. Crash reports are disabled in settings, yet it asks for permission and password to report.

PC1 : Empty trashcan shows non-empty icon. Right-click Empty Trash, something crashes and the error reporting query appears again, despite being disabled. 
Icon still non-empty, despite empty. This is a leftover from earlier versions where the same thing often happened.

PC2: VLC hangs in 4K with a big green screen filling the display. System still works in the background, but cannot switch with ALT+TAB or CTRL+ALT+F#. Had to hard reboot twice. Radeon Vega3 non-proprietary drivers. Does not seem to happen in 1920x1080 mode.

---

### Post by palteater on 2022-04-23
PC2: Brave browser stopped working. Crashes immediately on start, with an "Oh snap! Reload?" and a bubble up to the right that says "uBlock Origin crashed, click this bubble to reload".

Clicking the bubble just makes it return again and again. Reloading the page results in the same thing.

Brave works well on PC1 though. and uBlock Origin makes no fuss there neither in Brave nor in Firefox.

---

### Post by palteater on 2022-04-23
PC1: Installed Midori via Ubuntu Software. Changed my mind and tried uninstalling it. Failed because there were "no packages". 

sudo apt remove midori worked.

---

### Post by him610 on 2022-04-23
> Instead of filing bug reports and watch them vanish into cyberspace
They do not disappear!
They get recorded, assessed, given a priority, and eventually assigned to a software engineer who determines how to correct the defect, develops the corrective code, and tests the corrected code. 
It then gets handed off to a software tester who performs testing on the application, and makes sure no other defects have been inadvertently introduced. 
Then it gets assigned to an inline patch, update, or release. I may have missed something in the flow.
I would think that anything related to security gets top priority. 
There only so many hours in a day, and the Ubuntu software engineers probably have population constraints.
If a defect is not reported then how do you think it will ever get corrected?

---

### Post by palteater on 2022-04-23
Every one of the dozen bugs I have ever filed in my life just resulted in complete silence. I expect to be ignored.

I recently had a PCI-express compatibility disorder between a $1000 CAD vidcard and a $1000 Threadripper Pro motherboard where nVidia blamed ASUS who blamed nVidia until I shut up and walked away. Got another vidcard instead. One of the few cases where I actually got responses, coming to think of it.

---

### Post by QIII on 2022-04-23
What sort of a response did you expect to get?  How did you report the bugs?

I can tell you with fair degree of certainty that adding a laundry list of nebulous bugs on an end-user peer-to-peer support forum where nobody has anything to do with the development of Ubuntu and nobody is an employee of Canonical, LTD, will not get your bugs resolved.

Please continue to report bugs via apport or Launchpad.  Those methods are the appropriate ways to make sure that those who can correct bugs see the reports.  They won't see them here.

It is possible that none of your issues is a bona fide bug so much as something you simply need technical assistance with.  If that is the case, please start a thread for each item in a support area of the forums.  One subject per thread, please.

To avoid this becoming a tangled mess of answers to a laundry list, closed.

---

