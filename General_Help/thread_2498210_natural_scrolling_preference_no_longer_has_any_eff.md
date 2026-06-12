---
title: "natural scrolling preference no longer has any effect"
date: 2024-06-04
forum: General Help
---

### Post by macho3 on 2024-06-04
Changing my "natural scrolling" preference no longer has any effect, and I'm stuck in my non-preferred option (I think it is natural scrolling enabled but I'm not sure which is which: up goes up, down goes down).

This just happened after a reboot following a minor upgrade. I'm on 24.04 and Unity.

It doesn't matter whether I do System Settings >> Mouse & Touchpad >> Natural scrolling, or whether I do:
gsettings set org.gnome.desktop.peripherals.touchpad natural-scroll true # or false

Nothing changes.

Assuming this is a bug, I'm not even sure what package to report it against. Any help would be appreciated.

---

### Post by currentshaft on 2024-06-04
Are you selecting the "Touchpad" tab in Mouse & Touchpad setting, or are you changing the setting for "Mouse"?

---

### Post by romperstomper on 2024-08-28
I'm not the OP, but checking the tab was set to "Touchpad" fixed the problem for me. Thank you currentshaft!

---

### Post by currentshaft on 2024-08-28
> **romperstomper said:**
> I'm not the OP, but checking the tab was set to "Touchpad" fixed the problem for me. Thank you currentshaft!

The UI of that settings menu is very unintuitive. I hope GNOME (?) developers take notice.

---

