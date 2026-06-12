---
title: "How to keep cairo-dock on top of the panel?"
date: 2008-05-01
forum: General Help
---

### Post by vmalep on 2008-05-01
Hi everybody!

I am running Ubuntu 7.10 and I would like to have cairo-dock displayed in the middle of the gnome panel (the panel located on the top of the desktop).

However, as soon as I click on this top panel, cairo-dock get hidden behind.

Is there any way to keep cairo-dock visible on the top?

Thanks for any help and best regards,
Pierre

---

### Post by Zorael on 2008-05-01
Running Compiz? Tried adding it as 'always on top' under Window Rules, in ccsm?

---

### Post by vmalep on 2008-05-01
Thanks! This was the solution indeed.

I first installed ccsm:
```
sudo apt-get install compizconfig-settings-manager
```

Then I entered "type=DOCK & name=cairo-dock" in the "Above" field of the "Window rules" module (and to enable the module of course). See also [the explanation on wiki.compi-fusion.org]("http://wiki.compiz-fusion.org/WindowMatching")
------------------------
Updated:

To be noted that the solution does not seem very stable. After reboot, the cairo-dock window is again hidden behind the panel and I have to modify the "Above" field (add or remove "type=DOCK & " for example) in the Window rules module in ccsm to have this rule applied again... I will keep testing it.

BR
Pierre

---

### Post by soccermonster5 on 2008-05-29
This is my first post ever, but I think I've found something that works\\:D/  Someone used this for awn, and I seem to have it working for cairo too.  Here's the post for what they did:

[http://ubuntuforums.org/showpost.php?p=3370460&postcount=5]("http://ubuntuforums.org/showpost.php?p=3370460&postcount=5")

I added screenshots from my system - the dock is on the top panel...

Hope this helps!

---

