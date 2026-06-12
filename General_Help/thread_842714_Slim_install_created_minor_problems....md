---
title: "Slim install created minor problems..."
date: 2008-06-27
forum: General Help
---

### Post by El_Belgicano on 2008-06-27
Some days ago I installed the slim login manager to replace gdm, the point is there were programs that were launched by gdm that slim doesn't start by default (usb disk do not automount anymore, language was french has been changed to default and devilspie starts with wrong size of my background terminal)

I've no idea what I should change to make it work by default again, or what I should place in the .xinitrc file. (WM is openbox)

Any help appreciated ;)

---

### Post by El_Belgicano on 2008-07-24
devilspie and language have been fixed, just remains the automount of my drives...

---

### Post by picpak on 2008-07-25
Try putting this in your ~/.config/openbox/autostart.sh:

```
gnome-volume-manager &
```

:)

---

### Post by El_Belgicano on 2008-07-26
Got it already in my .xinitrc, but I'll try with the autostart.sh

---

