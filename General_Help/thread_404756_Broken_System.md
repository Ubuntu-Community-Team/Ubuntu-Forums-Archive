---
title: "Broken System"
date: 2007-04-08
forum: General Help
---

### Post by se2schul on 2007-04-08
I tried using ndiswrapper to install drivers for my usb wireless adapter, and along the way, I seem to have done something to break Ubuntu.  I'm a relative beginner with Ubuntu, and I don't know how to diagnose/repair problems.

I just installed Edgy on my laptop using the Alternate CD, then installed XFCE.  I immediately tried to get my wireless adapter to work.  I installed ndiswrapper using Synaptic, but I found that it didn't work. I used Synaptic to remove the ndiswrapper package. I blacklisted 3 modules (as suggested to me in another thread), and I downloaded and installed the latest ndiswrapper and managed to get my wireless adapter to connect to my WAP without WEP. I couldn't get WEP to work, and I decided to reboot my machine (it was a windows reflex ;)) .  When my computer came back up, I logged into XFCE, but I no longer had a task bar or anything. All I had was my blue background.

How do I go about diagnosing and repairing this problem? Should I just reinstall?

Thanks,
Steve

---

### Post by ffxr on 2007-04-08
i just think xfce crashed dont re install yet..

use ALT-F2 and try these each of these commands:

xfce4-session
xfdesktop
xfce4-panel

then when you restart remember to tick remember session settings.. that should sort you out, even after following reboots..


other thoughts, [this is not be essential, just an opinion]

id try and get native linux drivers for your wireless USB card.. ( i have this strange aversion to ndiswrapper & have never even tried it, i just dont like how it works, however clever the code)

if you want to use xfce ( & get the full benefits of its speedier interface, id install from a xubuntu alternate CD)

all the best.

---

### Post by se2schul on 2007-04-08
xfce4-panel fixed it!!
Thanks.
Why didn't those commands get run on reboot? Should they?

On your other thoughts, thanks. I'll consider these points in the very near future.

---

### Post by ffxr on 2007-04-08
xfce didnt save its settings on its way out during the reboot, it may have crashed.. it happens sometimes, particularly just after its been installed... if you remember to save settings on exit, it shouldnt occur again.. (well, not very often), just remember them commands, so you know how to recover next time you screw up xfce ; )

---

