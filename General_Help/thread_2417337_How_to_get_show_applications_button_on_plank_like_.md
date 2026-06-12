---
title: "How to get show applications button on plank like gnome 3 dock has?"
date: 2019-04-22
forum: General Help
---

### Post by jebi on 2019-04-22
hi

How to get show applications button on plank like gnome 3 dock has?

also anyone know a a way to force transparent windows settings to persist, i have tried lots of extensions but when you close the window and re-open the setting has defaulted?

thx

---

### Post by #&amp;thj^% on 2019-04-22
If your speaking of keeping open apps so they show on plank, just a right click on the the icon, and choose "keep in dock".
And there is always the hidden settings in **"plank --preferences" **where you can change themes, icon size, and a little more
Now if your speaking of a menu for all applications, install Docky.
For your transparent windows settings:
```
gsettings set org.gnome.shell.extensions.dash-to-dock transparency-mode FIXED
```
The above code _assumes_ you have "dash-to-dock" installed.

---

