---
title: "The vanishing panels"
date: 2007-11-23
forum: General Help
---

### Post by Lilyoftheshadow on 2007-11-23
I'm the rather satisfied owner of a new Gutsy/XP dual boot system... Except that there are some problems that I have a feeling are my fault.

I just had to reboot to restore the default top and bottom panels. They vanished completely on me without warning or error message. I don't know if I pressed a button or what. :confused: I think I may have done something because I have been fiddling with the SCIM anthy settings, trying to work it so that I can easily switch between Japanese and English input.

After reboot, they're both there, exactly as I left them. What was that, and how can I fix/prevent this from happening again?

---

### Post by GavinZac on 2007-11-23
perhaps gnome-panel simply crashed. if this is the case, it'll be pretty tough to find the cause, but it'll be fairly difficult to replicate anyway,

---

### Post by Lilyoftheshadow on 2007-11-23
I remember it happening before, when I was booting from the CD. Could this have been the same thing?

If so, is there any way to reboot the gnome-panel without a full reboot? Alt+F2 didn't launch anything like it was supposed to, that was the first thing I tried.

---

### Post by GavinZac on 2007-11-23
use the command "gnome-panel restart"

I think this will work, but it is based on a quick google search.

---

### Post by komputes on 2007-12-13
sudo debconf gnome-panel

Reboot and enjoy the default panels

:popcorn:

---

