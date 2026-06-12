---
title: "&quot;Appearance&quot; app freezing up"
date: 2008-02-15
forum: General Help
---

### Post by gfahey on 2008-02-15
Using 7.10 on Dell Vostro 1000 laptop and man, things are just going great but....

Whenever I go to System>Preferences>Appearance and try and install or customize or *anything* it freezes up and I have to force quit. The only way I can change wallpaper is to open an image in any editor (like GIMP) and choose to make it my desktop WP.

Can't seem to find a workaround on this and it used to be just fine until a few days ago. I'm guessing some conflict with another package I've downloaded but, have no clue otherwise. Any help appreciated.

---

### Post by FuturePilot on 2008-02-15
Do you have the gtk-qt-engine installed by chance?

---

### Post by gfahey on 2008-02-15
> **FuturePilot said:**
> Do you have the gtk-qt-engine installed by chance?

Thank you.....yes I do.

---

### Post by FuturePilot on 2008-02-15
Remove it. The gnome-appearance-properties doesn't seem to like that engine for some reason.
```
sudo apt-get remove --purge gtk-qt-engine
```

---

### Post by gfahey on 2008-02-15
> **FuturePilot said:**
> Remove it. The gnome-appearance-properties doesn't seem to like that engine for some reason.
```
sudo apt-get remove --purge gtk-qt-engine
```

That did it but, gdesklets still wont load. No big deal really. I can live without it. Thanks again.

---

