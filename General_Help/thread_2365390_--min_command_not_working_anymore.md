---
title: "--min command not working anymore"
date: 2017-07-06
forum: General Help
---

### Post by ardouronerous on 2017-07-06
I use Balabolka Portable from PortableApps.com ([portableapps.com/apps/accessibility/balabolka-portable]("https://portableapps.com/apps/accessibility/balabolka-portable")) as my Text-to-speech application on Xubuntu using PlayOnLinux.

Here's the command I use: [FONT=courier new]/usr/share/playonlinux/playonlinux --run "Balabolka Portable" %F --min[/FONT], the --min is suppose to start Balabolka minimized, it has worked before, but now, it doesn't seem to work anymore.

---

### Post by ardouronerous on 2017-07-06
I figure out what the problem was, Balabolka's minimize option doesn't work if the window is maximized, so I set it to unmaximized, so now --min works.

---

