---
title: "No title bar with Domino theme in kubuntu"
date: 2008-05-07
forum: General Help
---

### Post by Tiny Grasshopper on 2008-05-07
Let me know if anyone else has experienced this.

Kubuntu Hardy
Compiz enabled with Custom Effects
[Domino theme for KDE]("http://www.kde-look.org/content/show.php/Domino?content=42804")
[Daurora config for Domino]("http://www.kde-look.org/content/show.php/Daurora?content=65297")
Nvidia-glx new drivers enabled

I downloaded the [Domino theme for KDE]("http://www.kde-look.org/content/show.php/Domino?content=42804") compiled it, installed it and enabled it. It looks great, with the Daurora config for it. Except when I maximise the window. The title bar disappears. It's not white or transparent. It's actually not there. So if there's a window behind the maximised window I can interact with it in the space where the title bar would be.

I have tried it with Custom, Standard and Extra effects and with other configs for the theme as well. The behaviour is the same with Extra Effects. With Standard effects, the title bar is not visible but I can still interact with it. In poking around with it I could interact with it when it's custom sometimes as well.

Does this sound bug-worthy or is there are setting in that morass of a compiz-config-settings-manager that should workaround this somehow?

Also on a side note, in poking around on the compiz config settings manager, I've turned on a feature where I mouseover an inactive window and it reduces the opacity of all the windows covering it. now I can't find it to turn it off. I've tried turning off auto-raise, trailfocus and fading windows and it still seems to persist. I can only turn it off when I reset to defaults. I'm more concerned about figuring out what the setting actually is. Any assistance would be appreciated on that.

---

### Post by speedkx on 2008-05-27
I am also seeing this with the same config:
Hardy
KDE
compiz
Domino
nvidia-glx-new on 8400M GT

Most other themes work just fine. I've heard of a few Gnome themes having trouble with decorations on maximized windows too.

I think it's a Domino bug or it may just hit something in compiz that other themes don't use. Please if someone else is having the same issue drop a note and I'll take a look at Domino's internals.

---

### Post by ironflippy on 2008-05-29
Same deal here.

Kubu 8.04
Compiz Fusion
Domino (smooth domino variant, but the same thing happens in the default domino config)
ATI card, default drivers (whatever they happen to be, I want to say Radeon)

---

