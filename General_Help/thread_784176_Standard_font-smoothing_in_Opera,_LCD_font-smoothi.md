---
title: "Standard font-smoothing in Opera, LCD font-smoothing everwhere else."
date: 2008-05-06
forum: General Help
---

### Post by danlea on 2008-05-06
After Hardy Heron (8.04) install all fonts in Opera 9.50b are smoothed in one shade only (e.g. greyscale).  I had the same version of Opera installed prior to the upgrade and it was fine (LCD subpixel smoothing), and Firefox (and general Ubuntu) fonts are also fine.

Image attached - top is Firefox (good), bottom is Opera (not so good).

Incidentally I have ensured that the X Font option is disabled in opera:config.

---

### Post by danlea on 2008-05-07
Bump - if that even works on this forum.

---

### Post by danlea on 2008-05-07
I should note that neither Firefox nor Opera pay any attention to the Gnome font-smoothing settings - it's just Firefox does it's own sub-pixel smoothing and Opera doesn't (any more).

---

### Post by danlea on 2008-05-07
AND - terminal has the same problem.

---

### Post by danlea on 2008-05-07
Right, the bug was reported on the link below.  I just had noticed it with Opera rather than with terminal.

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/190848](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/190848)

---

### Post by lubiluk on 2008-05-07
Did you tried?
sudo dpkg-reconfigure fontconfig-config

---

### Post by arty on 2008-05-11
I've just fixed same problem. I have 'Other' folder in my apps menu, and there're 2 labels named 'Fonts'. First of them allows separate customization of anti-aliasing. It had default value of 'System settings', but when I changed it to 'enabled' and configured AA, everything started working fine.

---

### Post by waynemcl on 2008-05-12
> **arty said:**
> I've just fixed same problem. I have 'Other' folder in my apps menu, and there're 2 labels named 'Fonts'. First of them allows separate customization of anti-aliasing. It had default value of 'System settings', but when I changed it to 'enabled' and configured AA, everything started working fine.

Hi Arty, Where's those menu options? Ubuntu menu or Opera menu?

Thanks
W

---

