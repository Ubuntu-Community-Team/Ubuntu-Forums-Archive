---
title: "gtali game stuck in full screen mode"
date: 2008-07-10
forum: General Help
---

### Post by Convert on 2008-07-10
Running Ubuntu 8.04.  Need some help here.  I have wasted hours trying to get the game gtali (called Tali in the games menu) out of full screen mode.  I don't even know how it got into full screen mode since the game does not have a full screen menu choice.  Does anyone know where this setting is stored?  I have even tried fully uninstalling and then reinstalling the gnome-games package but it still starts up in full screen mode and there's no menu or command to get it out.  I know that the setting is tied to my ID because it doesn't run in full screen mode when I start the game up as root.

Extremely irritating.  Any help would be appreciated.

---

### Post by Activist on 2008-07-10
try changing the desktop resolution into a higher one, and then run the game see if again its in fullscreen..

if with that its fixed then the problem is the game resolution, wich might be higher than your desktop resolution.

---

### Post by Convert on 2008-07-10
> **Activist said:**
> try changing the desktop resolution into a higher one, and then run the game see if again its in fullscreen..

if with that its fixed then the problem is the game resolution, wich might be higher than your desktop resolution.
Thanks for the suggestion but that is not the problem.  First, my screen is already at the highest resolution it supports, so I can't switch to something higher (good suggestion, though).  Second, the game didn't start out in full screen mode, it switched to full screen mode while I was playing it.

I had this same problem with a different program in Ubuntu 7.10.  That problem was never fixed.  I suspect it is a problem with gconf.  If so, there's no documentation that will help.

The blurb on documentation:
"Documentation: This page introduces GConf - read on for some simple docs and FAQs and troubleshooting information. The GConf reference manual is sort of incomplete - a slightly old version can be found at [http://developer.gnome.org/doc/API/](http://developer.gnome.org/doc/API/). For now you should really use the version in the GConf tarball instead, it has some important updates."

No help there as far as I can see.

---

