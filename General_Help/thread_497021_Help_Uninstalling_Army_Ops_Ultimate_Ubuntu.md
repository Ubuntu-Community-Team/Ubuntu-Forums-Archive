---
title: "Help Uninstalling Army Ops Ultimate Ubuntu"
date: 2007-07-09
forum: General Help
---

### Post by CrankyFilipino on 2007-07-09
Ok so with the upgrade in Ultimate Ubuntu I've installed Americas Army, Army Ops whatever it is.. and now I just can't get rid of the damn thing. I can't delete it graphically because permission is denied and I can't find it in synaptic manager.. and I just want the damn thing gone off my system and I'm getting so frustrated I'm about to re-install the whole distro.. I also want to get rid of the non-working Wolfenstein that was installed and install it properly.. does anyone have any experience with this issues using Ultimate Ubuntu or have any idea how I can get rid of them? Thanks

---

### Post by bettlebrox on 2007-07-09
Hey Cranky!

If you *cd* to the directory where America's Army is installed and run the the uninstall command using sudo.

For example, if it's installed in /usr/local/games/armyops
[INDENT]cd /usr/local/games/armyops
sudo ./uninstall[/INDENT]

Which Wolfenstein game?

Luck!

---

### Post by CrankyFilipino on 2007-07-10
> **bettlebrox said:**
> Hey Cranky!

If you *cd* to the directory where America's Army is installed and run the the uninstall command using sudo.

For example, if it's installed in /usr/local/games/armyops
[INDENT]cd /usr/local/games/armyops
sudo ./uninstall[/INDENT]

Which Wolfenstein game?

Luck!

Aww crap.. I was excited at having this work but it doesn't have a suitable uninstall program! Now what do I try lol.. and it's the Enemy Territory Game.. thanks

---

### Post by ccal on 2007-07-10
> **CrankyFilipino said:**
> Aww crap.. I was excited at having this work but it doesn't have a suitable uninstall program! Now what do I try lol.. and it's the Enemy Territory Game.. thanks

You can delete the game's directory and  ~/.loki/installed/armyops.xml

---

### Post by CrankyFilipino on 2007-07-10
Thanks for the help.. while looking for a solution for something else.. I ended up using gksudo nautilus and deleting all the fies that have to do with it.. I also used that to fix my trash problem because I had lost many gigs of space without knowing why.. ha! Another great thing about linux.. is the lack of a damn registry.. now the registry is at heart a great idea for windows.. but it ended up being sucky and cluttered.. I love how the lack of having one in linux seems to make everything better for me..

---

