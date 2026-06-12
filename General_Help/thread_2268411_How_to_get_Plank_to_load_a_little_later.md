---
title: "How to get Plank to load a little later"
date: 2015-03-08
forum: General Help
---

### Post by Mazate on 2015-03-08
Howdy All

I use Plank and I have it load automatically when Ubuntu reloads.  The problem I have is that when I go to shut down, I have trouble because Ubuntu wants me to close down Plank first, otherwise I can just logout.  After reading online I discovered that this problem can be resolved if you can set Plank to wait a little longer to load when booting up.  Somehow that makes it so that it will shut down properly.  Does anyone know how to do this?  I figured it out a long time ago in Mint but I have no idea how to do it here.  Any help is most appreciated.  I'm using 14.04 LTS.

---

### Post by mc4man on 2015-03-08
If you are doing via an startup application created .desktop then open that .desktop in a text editor & add this line, adjust number as needed
```
X-GNOME-Autostart-Delay=3
```

Ex. of what I have  here, location/name is ~/.config/autostart/plank.desktop (your name may be different..
```
[Desktop Entry]
Type=Application
Exec=plank
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=plank
Comment=Plank
X-GNOME-Autostart-Delay=3 
```

---

### Post by Mazate on 2015-03-08
Yes, I used the "Startup Applications" app.  I'll try to hunt it down and open it with a text editor and let you know how it goes.

---

### Post by mc4man on 2015-03-08
> **Mazate said:**
> Yes, I used the "Startup Applications" app.  I'll try to hunt it down and open it with a text editor and let you know how it goes.

It will be in ~/.config/autostart 
Note that .desktop files can't be opened in gedit from the context menu so browse to location, have gedit open & just DnD the .desktop on to gedit window
(other means to open .desktop files in gedit are available but DnD will be fine..

---

