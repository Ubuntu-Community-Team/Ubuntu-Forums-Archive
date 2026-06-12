---
title: "Semi-fancy keyboards..."
date: 2007-05-21
forum: General Help
---

### Post by TheBuzzSaw on 2007-05-21
I have a keyboard with the extra row of keys along the top (browser functions, volume control, etc.). Most of them work fine, and I can even customize most of them. However, the big button in the center has a picture of a crescent moon. Whenever I press it, my computer attempts to go into standby mode. I have already learned from past experience that my computer cannot handle standby mode (even in Window&#4447;&#4448;s XP). I can never bring it back from this mode; I end up having to reboot (by powering completely down) anyway.

Regardless, I have no interest in fixing the standby mode. Rather, I am wondering if there is a way to reassign that moon key to be system shutdown instead. I have already played around with System > Preferences > Keyboard Shortcuts. There does not seem to be a standby or shutdown assignment available. Suggestions?

---

### Post by Ramses de Norre on 2007-05-21
Look into your acpi settings in /etc/acpi/, it might be configured somewhere there.

---

### Post by TheBuzzSaw on 2007-05-22
> **Ramses de Norre said:**
> Look into your acpi settings in /etc/acpi/, it might be configured somewhere there.
Hmmm... This looks good. It brought me one step closer, but I'm not sure what I'm looking at here. I've viewed several of the contained 'sh' files, but I don't know what to tweak. More help? :)

---

### Post by Ramses de Norre on 2007-05-22
I'm sorry I know you can change some of those settings there but I never tweaked acpi before myself so I can't help you any further.

---

