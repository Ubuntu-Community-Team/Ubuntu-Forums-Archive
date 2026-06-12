---
title: "Startup and Shutdown sounds for Gnome 3"
date: 2016-10-30
forum: General Help
---

### Post by ray42 on 2016-10-30
My startup and shutdown sounds do not work. Both startup and shutdown sounds are in their appropriate folders. How do I get them to work?

I have checked the following to no and it is already present.

[COLOR=#1A1A1A][FONT=Merriweather]STARTUP SOUND[/FONT][/COLOR]
[LIST=1]
[*]Make sure you have libcanberra installed
[*]If not present already, create .desktop file in /usr/share/gnome/autostart with the command,
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
[/LIST]

---

### Post by ray42 on 2017-01-14
bump

---

