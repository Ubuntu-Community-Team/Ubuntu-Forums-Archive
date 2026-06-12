---
title: "glx gears and graphics problem (ATI)"
date: 2008-02-15
forum: General Help
---

### Post by chaitanya.iit on 2008-02-15
[SIZE="3"]hi guys!!

I am having[SIZE="5"] ATI RC 410[/SIZE] graphics card
i have installed compiz settings manager and i have tried to change  appearence preferences -visual settings from none to custom .......it gave[SIZE="5"] desktop effects could not be enabled.............[/SIZE]
i ihave installed XGL and now the comp is running slowly when i am closing or opening windows

even the media player files are also not playing properly in vlc..


can u plzz help

[/SIZE]

---

### Post by DrMega on 2008-02-15
This happened to me when I installed XGL, mistaking it for something else.

You don't need XGL for desktop effects if your graphics card is reasonably up to date. As I understand it, XGL gives you OpenGL support for cards that don't support it in hardware or where the drivers aren't available.

If you are using the ATI driver, then you won't need XGL in order to get Compiz effects. In fact, XGL will just slow it down as it runs all your OpenGL in software rather than in hardware.

---

### Post by pointone on 2008-02-15
The version of the ATI proprietary fglrx driver in the repositories cannot run Compiz without Xgl. You need to update to the latest version of fglrx from the ATI website, or use the open source "radeon" driver if your card supports it.

However, the "graphics card" you refer to is actually an integrated video solution, and will not give you performance anywhere close to that of a dedicated GPU. Slowness is to be expected. Compiz isn't for everyone.

---

