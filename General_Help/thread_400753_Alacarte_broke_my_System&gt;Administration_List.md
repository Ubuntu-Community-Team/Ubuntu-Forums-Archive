---
title: "Alacarte broke my System&gt;Administration List"
date: 2007-04-03
forum: General Help
---

### Post by tj.milligan on 2007-04-03
Using Alacarte (aka Menu Layout) last week to *hide* certain apps that show up as duplicates or that I don't use, it managed to *hide* two-thirds of my Administration programs! When I run Alacarte, there is a check box next to "Show" for EVERY Administration program. To reiterate, these administrative programs show up in Alacarte only, not in System>Administration menu. All other menus are fine (Applications, Places and System>Preferences). How can I fix this? I want my Administrative program shortcuts back :( 

BTW, the programs that DO show up still are *Keyring Manager*, *Network Tools*, *Printing*, *System Log* and *Update Manager*.

Please Help! :confused:

---

### Post by tj.milligan on 2007-04-04
Bump. BTW the thread [http://ubuntuforums.org/showthread.php?t=346869&page=2](http://ubuntuforums.org/showthread.php?t=346869&page=2) only served to confuse the issue and remind me of how nice regedit seems in comparison** :\ Using the method described by Amaroq I recovered 2 more Admin programs in 2 hours. Still missing around 10... :(

** Sarcasm. One reason I switched to linux was to escape the horrible windows registry. However, this Alacarte problem is a black eye to an otherwise great desktop environment (gnome).

[B]EDIT --

FIXED! Did so many hacks I'm scared about the next update. Finally, right before I gave up for the night, I issued a gksu users-admin, clicked on my username and noticed there was no check next to "Administer the system." Checked it, and issued killall gnome-panel, and EVERYTHING is back![/B]

---

