---
title: "[SOLVED] Disable user change"
date: 2008-05-08
forum: General Help
---

### Post by rolodoom on 2008-05-08
How can I disable user change? I mean, want only one user at a time and not to leave open sessions.

---

### Post by garyedwardjohnston on 2008-05-08
Not sure what youre trying to do here but you can disable the login screen and make it automatically log in to the person of your choice.

As far as disbling the making of new users, don't make any and keep your password to yourself.  If noone knows your root password, noone can create user accounts.

---

### Post by sdennie on 2008-05-08
You should be able to disable it from the screensaver by using gconf-editor and going to /apps/gnome-screensaver and disable enable_user_switch.  To disable it from the logout menu, again use gconf-editor and go to /desktop/gnome/lockdown and disable user_switching.

---

