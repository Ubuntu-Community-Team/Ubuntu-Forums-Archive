---
title: "lxlauncher won't launch kde games"
date: 2014-07-11
forum: General Help
---

### Post by lykwydchykyn on 2014-07-11
Playing around with Lubuntu 14.04 on an old touchscreen system.

I configured lxlauncher to run at boot, and installed the kdegames metapackage.  When I try to launch kde games from the lxlauncher or the regular LXDE menu, about 3/4 of them won't launch.  There are no errors, nothing shows up in .xsession-errors or at console out put of lxlauncher.  They just don't run.

The very same games will run just fine if I open a terminal and launch them by name.

Some names of games that won't launch:

 - KPatience
 - KTuberling
 - KNetwalk
 - KMines
 - KMajongg

Kapman and Palepelli, and one or two others *will* launch from lxlauncher.  

I've tried restarting the session, rebooting, other trivial things like that.  It makes no difference.  Weird, huh?

---

### Post by lykwydchykyn on 2014-07-11
OK, I figured something out.

Looking at the .desktop files for these programs under /usr/share/applications, the command (Exec=) specified in the ones that *won't* launch contain arguments, e.g. "kblocks -caption %c".  The ones that *will* run contain just the executable name, with no arguments.

Perhaps it's time to file a bug.

EDIT: in case anyone else runs into this issue, the bug report is here: [https://bugs.launchpad.net/ubuntu/+source/lxlauncher/+bug/1340936](https://bugs.launchpad.net/ubuntu/+source/lxlauncher/+bug/1340936)

---

