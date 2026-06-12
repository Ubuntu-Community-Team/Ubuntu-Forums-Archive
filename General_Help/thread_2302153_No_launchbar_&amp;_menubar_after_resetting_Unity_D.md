---
title: "No launchbar &amp; menubar after resetting Unity DEFAULTS (15.10)"
date: 2015-11-08
forum: General Help
---

### Post by rtimai on 2015-11-08
Ubuntu 15.10 wily: I recently used Unity Tweak Tool to simply reset defaults in the "Unity" group of settings, which immediately crashed the launchbar and menubar, leaving an empty desktop. Restarting repeatedly resulted in an empty desktop. In case other users experience this problem after running Unity Tweak Tool, here is general information: 

If CompizConfig Settings Manager is not installed, install and then run it:
[Ctrl-Alt-T Terminal or Ctrl-Alt-F1 TTY1]

 sudo apt-get install compizconfig-settings-manager
 ccsm

Use CCSM to re-enable Unity plugin. There will be a warning that Gnome and Unity Settings conflict. Confirm all the changes to the conflict-resolution prompts. The first time I did this CCSM crashed, and I restarted and repeated the procedure successfully the second time, when the launchbar and menubar reappeared without requiring a restart.

This fix is only for systems in which Unity has been running properly, and then THEN crashed as a result of Gnome settings conflicting with Unity settings (caused by fiddling with Unity Tweak or CCSM.) The missing Unity launchbar/menubar symptom has occurred for  various reasons since Unity was first introduced (other reasons include video driver issues.) I just wanted to document this one user experience, that it can occur in wily 15.10 as well on established platforms. LESSON: Use Unity Tweak and CCSM with *extreme caution.*

---

### Post by darkzail on 2016-01-01
Thanks a lot.
Saved my day.

---

