---
title: "Is it Compiz?"
date: 2008-05-14
forum: General Help
---

### Post by anotherdisciple on 2008-05-14
I have a problem with anything that is graphics intense. My Desktop effects work great, but when I run a game like SuperTux or if I turn on visualization in a music program... the window blinks over and over. I've notice that it does it less when I disable the desktop effects.... but it still does it. Does anyone know what could cause this.

BTW- I have a 128MB ATI Mobility Radeon x1400, 2.0 GHz Centrino Duo Core, 2 Gigs of RAM

---

### Post by Luke has no name on 2008-05-14
Yes, it is Compiz. When you get into 3D mode (I guess) on ATI graphics cards, Compiz conflicts with it. You have to turn Compiz completely off to fix it while you use 3D programs. (System > Prefs > Appearance > Visual Effects > None)

There is also some "Fusion-icon" that can one-click toggle Compiz for easier switching, but I couldn't figure it out <_<

Yes, this is ATI only, which is unfortunate. I believe a bug report is out.

---

### Post by forestpixie on 2008-05-14
install fusion-icon and start it - it should live in the notification area

```
sudo apt-get install fusion-icon
```

After installation it can be found in system tools menu - it will start as a tray icon - right click it and choose metacity or compiz as window manager.

I used it once or twice but it interferes with the script I use so that I don't have slow menus ( a problem with compiz and nvidia afaik)

---

