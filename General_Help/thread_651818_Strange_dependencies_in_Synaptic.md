---
title: "Strange dependencies in Synaptic"
date: 2007-12-28
forum: General Help
---

### Post by oomingmak on 2007-12-28
I've been trying to remove some junk / unwanted files from my system. I started by following this HowTo guide  ([http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)) which all worked fine.

However despite having already run localepurge, I noticed that there were still foreign language packs installed that were of no use to me, so I thought I'd remove them using Synaptic.

One such package was libthai (Thai language support) but when I marked it for removal, synaptic then marked about 100 other items for removal as well (basically the entire OS). This included all of Open Office, alacarte, compiz, file roller, firefox, gimp, a whole multitude of gnome and gtk apps, metacity, nautilus, synaptic and the list goes on.

Why is synaptic trying to eviscerate the *entire* OS when all I want to do is remove Thai language support?

:confused:

I understand that packages have dependencies, but how could virtually the whole OS depend upon the presence of Thai language support in order for it to work?

---

