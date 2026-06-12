---
title: "Unity suddenly died halfway through update"
date: 2014-03-16
forum: General Help
---

### Post by dimitar3 on 2014-03-16
Hello everyone!

My first post on these forums and sadly it's a desperate call for help. I'm halfway through upgrading my Ubuntu from 12.04 to 12.10 but during the upgrade my whole Unity including Launch panel, taskbar, Alt+Tab combinations and all that just died. Here's a screenshot of what my desktop currently looks like. I'm using the integrated title bars and buttons so I'm pretty much unable to minimize/close any of the windows. Any tips?

[http://ubuntuone.com/38rv9wPgyjVS5BWLmDNYIE](http://ubuntuone.com/38rv9wPgyjVS5BWLmDNYIE)

It's very likely that this might not be related to the upgrade, but it's the first time that anything like this happens that's why I believe it might be related.

Thanks!

---

### Post by bapoumba on 2014-03-16
Well, if you are in the middle of the upgrade, I'd say let it complete. Before you reboot, check your /etc/apt/source.list file, make sure all is set up for Quantal, may be run **sudo apt-get update **and **sudo apt-get upgrade** to make sure you are all up to date before rebooting (if upgrades are due, apply them and update/upgrade again until it says no files to upgrade), and choose a default session at login.

---

### Post by dimitar3 on 2014-03-16
Right, thanks for the quick answer bapomba! Waiting for the upgrade to finish sounds like the logical thing to do. I don't think I will have the time to run the update command as it seems that at the end of the upgrade there will be an automatic restart, but I definitely will do afterwards.

---

### Post by howefield on 2014-03-16
Just out of interest, why are you upgrading to 12.10 ?

---

### Post by bapoumba on 2014-03-16
> **dimitar3 said:**
> Right, thanks for the quick answer bapomba! Waiting for the upgrade to finish sounds like the logical thing to do. I don't think I will have the time to run the update command as it seems that at the end of the upgrade there will be an automatic restart, but I definitely will do afterwards.

Well, even if I upgraded a coupe days ago, I do not remember :D
I did run the update/upgrade from a terminal window before I rebooted. So hopefully you'll have the option to say OK reboot. From the first debian days, I've always checked upgrades before restarting. In the old days, I remember I could run update/upgrade several times before everything was on par. Not anymore, but I kept the habit :)

---

### Post by bapoumba on 2014-03-16
> **howefield said:**
> Just out of interest, why are you upgrading to 12.10 ?
Yes, good question, but for now they are in the middle of it..

---

### Post by howefield on 2014-03-16
> **bapoumba said:**
> ...but for now they are in the middle of it..

Nothing wrong with your powers of observation then :)

---

### Post by bapoumba on 2014-03-16
> **howefield said:**
> Nothing wrong with your powers of observation then :)

Eheh, I'm sometimes concerned. How could I forget how the upgrade ended two days ago? I did look at the sources.list and run an update/upgrade to make sure, but I have no recollection whatsoever of how the upgrade process itself ended up. Well, once they are good, it will be time to move to a supported release :)

---

