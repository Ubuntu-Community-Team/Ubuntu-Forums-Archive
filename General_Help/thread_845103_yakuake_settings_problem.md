---
title: "yakuake settings problem"
date: 2008-06-30
forum: General Help
---

### Post by Saisin-Tae on 2008-06-30
Problem: Yakuake does not save settings. Every time I start yakuake, all the settings like scheme, system bell or such return to what they were when I first ran the application. These settings are, however, different from the ones Konsole uses. My konsole is configured to have transparent scheme with dark background and blinking cursor with system bell turned off, while yakuake has white background with black text and system bell on. This notably resembles the settings that the gnome Terminal uses, so I tried changing it's config to see what happens, but unfortunately nothing happened. Changing yakuakerc  does not seem to have any effect either, and neither does changing krc, so I am at a loss as for what to do. Every time I open the yakuake terminal, the settings simply seem to disappear and I have to reconfigure it once again, not even mentioning that opening every single new tab means having to repeat the process all over again. Many of you might think that I simply forgot about the "save as default" option, but believe me, that is not the case. The only hint I have is that the application seemed to have some kind of problem when I first tried to run it (opened only under root privilegies) but fortunately nothing of the sort happened again, so I doubt this has any relation to the current problem at all.

---

### Post by Saisin-Tae on 2008-06-30
hmmm... if I run the application under the root permissions, it seems to be able to save the settings. Unfortunately, these do not apply to the "normal" yakuake, only to the su- one. Maybe some problem with the permissions?... Oo

---

