---
title: "Kodi keep to autostart whereas I removed kodi.desktop"
date: 2020-01-21
forum: General Help
---

### Post by LeBabe on 2020-01-21
Hi,

I have a Lubuntu installed with autologin user and autostart kodi.
I tried to stop the kodi autostart but I don't know it keeps running just after autologin.

To enable autostart I created this file : /home/user/.config/autostart/kodi.desktop
inside I put this :

```
[Desktop Entry]
Type=Application
Exec=kodi -d 30
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=false
Name[en_En]=kodi
Name=kodi
Comment[en_En]=
Comment=
```

I removed this file but kodi keep running at startup.
How to know what is launching it?

Thanks by advance

---

