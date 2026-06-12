---
title: "Ubuntu suspends when laptop lid is closed"
date: 2015-01-23
forum: General Help
---

### Post by raz3r2 on 2015-01-23
Hello,

I am using Ubuntu 14.10 and recently I encountered this problem. When I close the lid of my laptop, system suspends even if I chose "do nothing" in the power settings. 

I tried two solutions: 
- First, editing the line "HandleLidSwitch=ignore" in /etc/systemd/logind.conf - Second, editing file /etc/UPower/UPower.conf and changing IgnoreLid=false, to IgnoreLid=true

None of this works in a way that I want. After first solution, when I close the lid, screen is turning off and locksreen is enabled (and that is what it should be). But after a few moments in lock screen, system is logging out and I am back on... well login screen. 

After second solution when I close the lid screen is turning off, but it isn't locking (so when I open the lid I don't have to type my password). When I manually lock screen (with combnation ctrl+alt+l) after few seconds screen is turning off and system is logging out. 

Why is this happening? If i lock my screen I want my system to stay in lock screen and not logging out.

It may be relevant, that this problem occured after I installed gnome-shell alongside unity (simply by typing sudo apt-get install gnome-shell). So I suppose that something from gnome-shell messed up with my system, but I have no clue what this could be. I tried to uninstall gnome-shell (by typing sudo apt-get remove gnome-shell), but of course this didn't remove all the dependecies (and I don't know what I can safely remove without breaking unity).

EDIT: I changed display manager from lightdm to gdm and on gdm everething is fine. So it seems the problem lies in lightdm. Or so it seems.

---

