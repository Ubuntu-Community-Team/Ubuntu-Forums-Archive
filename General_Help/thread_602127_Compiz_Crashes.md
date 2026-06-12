---
title: "Compiz Crashes"
date: 2007-11-03
forum: General Help
---

### Post by _Strike_ on 2007-11-03
Yesterday I attempted to backup my CCSM profile. Unfortunately after I named the file and clicked on "Save" CCSM crashed (leaving no profile file).

If I run CCSM from the Terminal and do the above I get the following error:
```
*** stack smashing detected ***: /usr/bin/python terminated
Aborted (core dumped)
```


The main problem occurred when I logged in to my Compiz/Gnome session today. The desktop loaded fine until there was what seemed to be some kind of refresh. The panels went blank, with a gray smudge over where the menu bar should be. I could still see my wallpaper and move the pointer, but nothing was clickable. The problem still persisted after restarting.

Luckily my Metacity/Gnome session still works so it isn't a crippling problem. I've tried reinstalling XGL (I'm using the ATi restricted driver) but that failed to fix anything. I would try reinstalling Compiz but then the profile backup problem gets in the way.

What confuses me is that I had Compiz running perfectly fine before. My only theory is that the CCSM crash broke something in Compiz. Otherwise, I have no idea.

Any help would be greatly appreciated.

Ubuntu 7.10 (gutsy)
Ati Radeon Xpress 200m

Edit: I forgot to mention that if I return to the login screen using ctrl-alt-backspace after Compiz crashes, then login to my Metacity/Gnome session, CPU usage is maxed. According to System Monitor the culprits are two compiz-real processes, which I must kill to normalize the CPU.

---

