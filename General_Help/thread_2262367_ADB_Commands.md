---
title: "ADB Commands"
date: 2015-01-24
forum: General Help
---

### Post by kevin141 on 2015-01-24
When i try to install adb commands via terminal, i would obviously have to enter this command

---> [COLOR=#333333][FONT=Courier]sudo add-apt-repository ppa:phablet-team/tools && sudo apt-get update [/FONT][/COLOR]<---[COLOR=#333333][FONT=Courier]

[/FONT][/COLOR]but i after it finishes "hitting ports" i get the response ---> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main earmuff packages 404 not found <---

are there not adb tools for armhf?
please help
thanks

---

### Post by oldos2er on 2015-01-24
Moved to General Help.

 The phablet-team PPA only has repositories for Utopic and Vivid, not Precise.

---

### Post by Andrew_Lucas on 2015-01-25
Idk if this is helpful, but adb/fastboot are available in the repositories under 'android-tools-adb' and 'android-tools-fastboot' respectively. The fastboot version is fine (at least I've not encountered any problems), but the adb version is one minor version out of date (and either the whole thing or sideloading only doesn't work with TWRP, I can't remember which). Googling will provide an XDA thread, with a binary available for adb, which works without problem.

---

