---
title: "Need troubleshooting help - feisty - stellarium"
date: 2007-05-05
forum: General Help
---

### Post by DaveRowell on 2007-05-05
I've installed Stellarium 0.8.2 using Synaptics.  Install went fine.  Link to app is installed in Applications menu.

When I run Stellarium - after a few seconds the screen goes black - I'm back to the desktop with the wrong (lower) screen resolution

Running from a terminal - screen goes black - terminal window reappears in screen of wrong resolution - here are the messages I get

david@CompaqSR1265:~$ stellarium
 -------------------------------------------------------
[ This is Stellarium 0.8.2 - [http://www.stellarium.org](http://www.stellarium.org) ]
[ Copyright (C) 2000-2006 Fabien Chereau et al         ]
 -------------------------------------------------------
Application locale is en
Localizing TUI for locale: en
Loading Solar System data...(loaded)
Loading location: "Paris", on Earth (landscape is: "guereins")
Loading Hipparcos star data...(118217 stars loaded [2200 dropped]).
Loading Hipparcos double stars...(8824 stars loaded)
Loading Hipparcos periodic variable stars...(1930 stars loaded)
Load star names from /usr/share/stellarium/data/sky_cultures/western/star_names.fab
Loading NGC data... (13226 items loaded [3175 dropped])

...no position data for Barnard's galaxy
...no position data for Papillon
...no position data for &#947; Cas nebulaLoading NGC name data...( 225 names loaded)
Loading Nebula Textures...(75 textures loaded)
Segmentation fault (core dumped)
david@CompaqSR1265:~$ 

Would someone please explain to me how to begin to troubleshoot this problem?

---

### Post by taurus on 2007-05-05
What video card do you have and have you installed a driver for it?

```
lspci
```

---

### Post by DaveRowell on 2007-05-05
lspci gives me:
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
among a myriad of other stuff

I assume that a driver is installed since I have no problems with other graphic programs.

David Rowell

---

