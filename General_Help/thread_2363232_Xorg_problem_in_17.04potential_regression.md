---
title: "Xorg problem in 17.04/potential regression"
date: 2017-06-07
forum: General Help
---

### Post by Kushal_Seetharam on 2017-06-07
[COLOR=#111111][FONT=Ubuntu]I had set up an xorg config file for my Evoluent Vertical Mouse that remapped some buttons and set the middle button to emulate wheel. After upgrading from 16.04 to 17.04, the emulate wheel setting no longer seems to work. I've attached both the config file and the Xorg.0.log. Both button mapping and wheel emulation are properly registered in the log, but while the button mapping works (tested using xinput or xev), the wheel emulation does not. I tried reinstalling xserver-xorg-input-all in case the package broke during upgrading but that didn't work.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]config file (placed in usr/share/X11/xorg.conf.d): [http://s000.tinyupload.com/index.php?file_id=14704395166047496194](http://s000.tinyupload.com/index.php?file_id=14704395166047496194)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Xorg.0.log file: [http://s000.tinyupload.com/index.php?file_id=09959637787522222124](http://s000.tinyupload.com/index.php?file_id=09959637787522222124)[/FONT][/COLOR]

---

