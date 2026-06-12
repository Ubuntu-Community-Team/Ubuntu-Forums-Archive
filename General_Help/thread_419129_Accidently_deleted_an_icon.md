---
title: "Accidently deleted an icon"
date: 2007-04-22
forum: General Help
---

### Post by Orange Juice on 2007-04-22
So, something happened and my Updates and Network Manager icons are missing. How do I get them back? I tried looking in "+ Add to Panel" but they aren't there, and I tried reinstalling Network Manager through Automatix, but it didn't restore the lost icons. I am using Ubuntu Edgy 6.10.

---

### Post by jordanmthomas on 2007-04-22
```
nm-applet --sm-disable
```
Are you talking about your tray icon being missing?
If so, this will put it back.

If it works, add this command by running gnome-session-properties and going to the startup tab and you should be set.

**you'll also need to make sure you have a notification area applet added to your panel.

---

