---
title: "How to safely uninstall a program with plugins installed?"
date: 2015-04-18
forum: General Help
---

### Post by arroy_0209 on 2015-04-18
I am using lubuntu and for doing latex (a software for preparing documents) related work I first installed gedit editor and then installed latex-plugin for gedit. Not I realize this was a bad approach since this combination has bugs which are very hard to solve and I feel easier way now is to uninstall the latex plugin. I have two options: either uninstall both gedit and the plugin or just uninstall the plugin and keep the gedit editor which I can use for some other purpose. Which option is better? Please note that earlier I had installed latex which is very big and while installing lated plugin for gedit, some other components of latex were also installed. Is it safe to remove these extra latex-related components without affecting latex installation in its current form?

---

### Post by mc4man on 2015-04-18
You can remove the gedit plugin, nothing will be affected & nothing else will be removed. 
It's possible that after removing the plugin some of the packages that were installed with it will now be eligible for autoremove. Whether you want to remove them is up to you, if so it's likely to have no negative affect.

---

