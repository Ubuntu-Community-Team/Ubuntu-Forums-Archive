---
title: "screen res problem after blackout"
date: 2008-07-03
forum: General Help
---

### Post by krowmagnum on 2008-07-03
I had a power outage for about a second and my machine shut down. The screen resolution dropped to 640x480 after using 1024x768 for some time. No larger choices for resolution in the system prefs.

After rebooting a couple of times I now have 800x600 and some smaller resolutions to choose from but I really need the 1024x768.

I have an AMD 32bit PC with a nVidia Geforce2 MX card and have the nVidia drivers loaded already. (Ubuntu 8.0.4)

Any ideas on what to do ? Should I reload the drivers ?

I honestly do not know where to begin.

Thanks in advance for any suggestions.

---

### Post by avtolle on 2008-07-03
Try this: from the CLI (Applications>>Accessories>>Terminal) type```
gksudo displayconfig-gtk
```, see if your monitor is properly detected by the system; if not, scroll through the list of vendors and models to find it, and if found, select and apply. While you are there, click on the graphics card tab and be sure that the card (type of card) is properly detected. Once finished, restart the system, and see if the changes have been applied.

---

### Post by krowmagnum on 2008-07-03
> **avtolle said:**
> Try this: from the CLI (Applications>>Accessories>>Terminal) type```
gksudo displayconfig-gtk
```, see if your monitor is properly detected by the system; if not, scroll through the list of vendors and models to find it, and if found, select and apply. While you are there, click on the graphics card tab and be sure that the card (type of card) is properly detected. Once finished, restart the system, and see if the changes have been applied.

Thanks, the monitor was on the generic setting and I found another one that works, (the video card was correctly identified)

Now I'm happily back to a resolution I can use. Thanks for the help.

---

