---
title: "Problems with WoW on Cedega"
date: 2008-03-11
forum: General Help
---

### Post by bluekage on 2008-03-11
So, like many people around here it seems, Im only hanging on to windows for World of Warcraft. Recently I've tried getting it running on Ubuntu with Wine and I seem to be one of the unlucky ones that can't get it to work.

Recently a friend suggested I try with Cedega, and after mucking around with it a bit I can finally play, but I still have a few problems. The smallest of which is my frame rate. It seems to only be down a small bit from windows and is not bad enough to where I cant play. I've read that disabling "IOMMU" may fix this, but I havent been able to figure out how to go about this, nor do I know if its even something I should do.

Secondly, I use WoWhead.com almost religiously, while the game is running I am unable to alt-tab out. I have tried setting the game to run in windowed mode, but this only causes the game to crash.

To wrap it up,
1. How do I disable IOMMU, and is it something that I should do?
2. How can I get WoW to minimize, or run in windowed mode without crashing?

Thanks in advance.

---

### Post by chadeldridge on 2008-03-13
I am still playing wow on Cedega as well, so I can help a bit.  Once you get it setup though, never update and never muck with its settings... its a PITA to setup over and over again.

1.  Use engine 6.0.2 / Win98 Mode / Pthreads auto / desktop no / xrandr / managed / mozilla control / scheduler no / decrease wineserver pri / accelerated interprocess / freetype xrender

2.  Run the game with the command line option -d3d in the cedega setup and the wow config file.




As far as I know unless you run windowed you cant get back to the graphical shell without killing cedega.

Hope this helps.

---

