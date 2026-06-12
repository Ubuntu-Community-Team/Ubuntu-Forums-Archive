---
title: "madwifi and fglrx running at the same time?"
date: 2005-10-23
forum: General Help
---

### Post by munkymonkjr on 2005-10-23
So my lappy calls for both madwifi and fglrx to run at the same time, but from what i could find, i can only do one or the other. In other words, i need restricted modules to run madwifi, but fglrx won't run as long as that package is installed. What am i missing here?

There was one alternative method i've thought of and thats to keep the restricted modules, remove all fglrx stuff. reboot. then alien and install one of those rpm packages from ati.com, lol...wishful thinking. any ideas?

on a side note, i want only ath0 and not eth0 to start during boot as that will save me on boot times a lot (since the laptop is hardly ever plugged into the router and almost always is on wireless).

any thoughts or ideas?

using a clean install of breezy
wifi card is gigabyte gn-wpeag
video is ati 9700 128mb on a 15.4" wxga 1280x800 screen

---

### Post by munkymonkjr on 2005-10-23
ok lol,. i realize some of you may be confused. you think that the restricted modules have fglrx and madwifi and you don't understand m y question. i need the LATEST ati drivers because the ones that come with restricted modules screw up my widescreen resolution.

---

### Post by munkymonkjr on 2005-10-23
w00t! 

So its all fixed now. I installed fglrx (latest version, not restricted modules). I got wireless working via ndiswrapper, madwifi would have been better i suppose, but ndiswrapper works too. Hell, I even went as far as to build a custom kernel that support hibernate (Suspend2). Even that one works but there is an issue.

As you know ATI's fglrx does NOT support suspend, so if my driver in xorg.conf is set to "ati"  i can suspend and unsuspend freely and it works like god wanted it to. However, fglrx causes issues. That said... anyone know a fix for fglrx + suspend that will make it work?

---

