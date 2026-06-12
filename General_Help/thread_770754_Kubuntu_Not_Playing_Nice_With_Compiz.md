---
title: "Kubuntu Not Playing Nice With Compiz"
date: 2008-04-27
forum: General Help
---

### Post by Bionic Apple on 2008-04-27
My kubuntu 8.04 installation is great, but KDE 3.5 is not working with Compiz-Fusion.  The problems started when I entered the desktop-effects menu.  I would click install, but absolutely nothing would happen.  Then when it finally was installed (I used the package manager), it saying that it was not installed.  It doesn't matter though, because I don't have to enter that menu again.  However, the effects of Compiz is clear.  Now, whenever I boot-up kubuntu the screen is black for 3 seconds.  Also, you know those bouncing icons under your mouse that appear when you start a program?  Now there is sometimes a black box behind them.  When I logout, the area under the transition area of the "black-out" effect is black.  

Is there a simple way to fix this?  Is this a distro-specific problem?  All I want are basic transition effects when minimizing and changing workspaces, so is there another way to get those effects without using the cpu/gpu-heavy compiz?  Should I just install kubuntu kde 4 and wait for the new kwin?

---

### Post by Zorael on 2008-04-27
I believe the screen goes black just as Compiz is started, when it replaces the default window manager, kwin. So I'm not sure there's a way around that. Perhaps if you managed to make KDE launch compiz instead of kwin to begin with.

As for the shadowfade effect being buggy; not distro-specific, but I believe there is some workaround where you can exempt the effect in the compiz settings manager. In Hardy, with the login/logout plugin, this workaround is there by default, though for the KDE4 logout effect.

I'm not at my kubuntu box at the moment, but it may be possible to run xwininfo in a terminal, then somehow evoke the fade, then click the fade itself. That will, hopefully, output information about the fade effect to the terminal - its title, its class - with which we could make the Fade Windows plugin exclude it.

---

