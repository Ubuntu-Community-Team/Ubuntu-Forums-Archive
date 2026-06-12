---
title: "Screen lock won't turn on"
date: 2013-10-31
forum: General Help
---

### Post by mandala1111-ram on 2013-10-31
I have been giving Unity another try after previous versions have been a bit buggy on my laptop and have been very impressed with the stability and speed of 13.10.The only little glitch I have come across so far is the lock screen on/off button won't move and is stuck on off.This is the first time this has ever happened with any Linux distro I have been running.Anyone else had this problem and know of any fix ?

  Cheers 
  Shane

---

### Post by TQLeaman on 2013-11-01
Hi,

You could try turning it off via dconf Editor and see if that resolves the problem.

Install dconf Editor (if you haven't got it):
[INDENT]Via Terminal:
[INDENT]sudo apt-get install dconf-editor[/INDENT]
OR
[INDENT]Use Ubuntu Software Centre to search for it.[/INDENT]
[/INDENT]

Run dconf Editor and navigate to:
[INDENT]org > gnome > desktop > screensaver[/INDENT]

Tick:
[INDENT]"lock-enabled".[/INDENT]

Hope that helps,

TQ

---

