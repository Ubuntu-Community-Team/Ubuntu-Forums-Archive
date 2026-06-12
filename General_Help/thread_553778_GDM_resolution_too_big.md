---
title: "GDM resolution too big"
date: 2007-09-18
forum: General Help
---

### Post by mattgaunt on 2007-09-18
The login screen on feisty has the wrong resolution as i can sort of scroll down past the menu bar at the bottom of the screen.

This did happen with my desktop as well when i first installed nvidia drivers and set-up twinview but this was fixed by changing the resolution on gnome under the settings.

Ive tried playing arnd with my xorg file but no luck in fixing the login screen.

Im pretty sure its just the resolution of it, just dont know how to set it

Does anyone have any ideas??

Matt

---

### Post by dcstar on 2007-09-19
> **mattgaunt said:**
> The login screen on feisty has the wrong resolution as i can sort of scroll down past the menu bar at the bottom of the screen.

This did happen with my desktop as well when i first installed nvidia drivers and set-up twinview but this was fixed by changing the resolution on gnome under the settings.

Ive tried playing arnd with my xorg file but no luck in fixing the login screen.

Im pretty sure its just the resolution of it, just dont know how to set it

Does anyone have any ideas??

Matt

It is because you have "Virtual" resolutions in your xorg.conf file that Ubuntu is trying to use.

If you manually remove some of the resolution settings (just have the "native" res and a few others) then the problem should go away.

As an example, mine has just the following:
```
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
```
and once I removed the resolutions between 1440x900 and 1024x768, the problem went away on my system.

---

