---
title: "Ubuntu 18.04 Automatic login not working"
date: 2020-04-12
forum: General Help
---

### Post by ChrisMacor on 2020-04-12
I'm trying to get rid of the login requirement everytime the computer goes to sleep or restarts.

I set automatic login on in account settings
and 
these entries in terminal

gsettings get org.gnome.desktop.screensaver ubuntu-lock-on-suspend
true
[LEFT][COLOR=#242729][FONT=Arial]If the result is true then set it to false using:[/FONT][/COLOR][/LEFT]
gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend false

still asking for password

Any suggestions?
Thanks,
Christopher

---

