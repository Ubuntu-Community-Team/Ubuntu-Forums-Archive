---
title: "Change DASH Label?"
date: 2014-09-28
forum: General Help
---

### Post by echotech2 on 2014-09-28
Is it possible to change the labels shown under the icons in the DASH?  For example, change "GTK UVC video viewer" to "Camera".

  --Dave

---

### Post by mc4man on 2014-09-28
That is controlled *usually* by the Name= line in the apps's .desktop, sometimes other lines are involved.
So in the case of guvcview.desktop what's shown in the Dash is what's on the X-GNOME-FullName= line

To change - 
```
sudo -H gedit /usr/share/applications/guvcview.desktop
```

Edit the "X-GNOME-FullName=GTK UVC video viewer"  to whatever you wish for your language, english is first one , ex.

> [Desktop Entry]
Name=guvcview
GenericName=GTK UVC video viewer
[COLOR="#0000CD"]X-GNOME-FullName=Camera[/COLOR]
X-GNOME-FullName[cs]=Prohlíže&#269; videa GTK UVC
...ect.
You may need a log out/in to see.

---

### Post by echotech2 on 2014-09-28
Thanks mc4Man, works as advertised.

---

