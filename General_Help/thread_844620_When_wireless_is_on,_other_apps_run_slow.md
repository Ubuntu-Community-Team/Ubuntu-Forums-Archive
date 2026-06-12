---
title: "When wireless is on, other apps run slow"
date: 2008-06-29
forum: General Help
---

### Post by DixieWolf on 2008-06-29
This is about the weirdest problem I've come across. when i have wireless enabled, other apps run slow.

For example, if I right click on a panel and then click properties, it takes
less than a second to open with wireless off. With wireless, it could be 5-20 seconds before anything happens. It seems to only happen when an already running program has to open another dialog (like clicking the Open or Save dialogs in any other program)

& its not a problem with gnome. i tested on FVWM as well. I installed a newer wireless driver, and it didn't help. I've tried two versions of the kernel. Anybody have any ideas of what to try next?

---

### Post by pytheas22 on 2008-06-29
Did you look at dmesg?  Maybe it would explain what's going on.

---

### Post by DixieWolf on 2008-06-29
well, i checked dmesg, and i didn't see anything that seemed to tell me anything... but i'll post my dmesg and see if anyone else sees anything.

i attached a tar with the full dmesg, and a dmesg just of the references to wlan0.

[ATTACH]75753[/ATTACH]

---

### Post by pytheas22 on 2008-06-29
I'm not sure if it's the problem, but I notice that your wireless connection is getting deauthenticated and reathenticated multiple times.  Do you know that this happening--in other words do you lose your connection for a few seconds frequently?  It's not occurring an absurd amount of times, but it seems to happen more often than it should.  If it happens very frequently, I guess that having to reconnect constantly could be tying up all of your machine's resources and making other things run slowly.

---

### Post by DixieWolf on 2008-06-30
yea, thats because our internet went down and i had to reset the wireless a few times. i'm totally stumped about why this is happening. I even switched network managers just to be sure that the network manager software wasn't going haywire.

---

### Post by danwood76 on 2008-06-30
What wifi card is it and what spec is your system?
Also what type of wireless encryption are you using?

---

### Post by pytheas22 on 2008-06-30
Also did you look at your processes to see if any one is tying up more CPU or memory than it should?  You can use the command "top" or the GUI at System>Administration>System Monitor to monitor system resource usage.

---

### Post by DixieWolf on 2008-06-30
my wireless card is intel. the module for it is iwl3945
the wireless security is WPA with TKIP. 

as far as cpu usage, it doesn't seem abnormal, but then again
hardy has always been a bit of a hog on my machine

EDIT: nevermind. i ended up installing another distro earlier,
mostly because of some other issues. Thanks for the help though.

---

### Post by Arcadian on 2008-07-01
Would have been interested to know what your wireless config thought it was at the time e.g. iwconfig wlan0

I've noticed slow desktop/window manager reponse times in an earlier version when networking settings weren't quite right. Particularly if a LAN card was enabled but not actually connected. Good luck with your new distro :)

---

