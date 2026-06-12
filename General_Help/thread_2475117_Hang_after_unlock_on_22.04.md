---
title: "Hang after unlock on 22.04?"
date: 2022-05-17
forum: General Help
---

### Post by csete on 2022-05-17
Hello,

I've been running very stable for a while now on 22.04 (upgraded from earlier version), but today I've had my machine freeze twice when unlocking from the lock screen.  The mouse is dead and nothing else seems to be able to work on the desktop.  I am able to get to a virtual terminal to restart the machine, but something is clearly not quite right.  Are there any currently known issues related to freeze after unlock?  Does anyone have any suggestions on how to diagnose this problem?

Up to date Ubuntu 22.04,  Wayland,  Intel graphics selected via prime-select ( Intel Corporation CometLake-H GT2 [UHD Graphics] (rev 05))

Thanks for any suggestions!
Craig

---

### Post by csete on 2022-05-18
Based on comments I found elsewhere, I did a dist-upgrade and at least at the moment things seems to have stablized.

---

### Post by csete on 2022-05-19
I guess I jumped to conclusions too quickly.  This started happening again this morning.  I also just noticed that even if I get a virtual terminal, I'm finding that attempting an `/bin/halt` does not completely finish the shut down either.  It seems like something is wedged, but I'm not sure where to start looking.  I could really use some pointers.

---

