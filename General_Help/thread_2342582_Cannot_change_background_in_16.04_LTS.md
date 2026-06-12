---
title: "Cannot change background in 16.04 LTS"
date: 2016-11-08
forum: General Help
---

### Post by Edward_Diener on 2016-11-08
Bringing up the system settings the background is a solid color, but the actual background I am seeing is some sort of purplish wallpaper with "Ubunrtu 16.04 LTS" written in the lower left corner area. How can I convince Ubuntu to use the solid color I have set in my Appearance | Background ?

---

### Post by CantankRus on 2016-11-08
You have to select colours & gradients from the drop down then one of the 3 gradient options.
The first box is a solid colour.
If you select one of the gradient options you will then be able to pick a second colour.
[ATTACH=CONFIG]272043[/ATTACH] [ATTACH=CONFIG]272044[/ATTACH]


If still doesn't work then make sure nautilus is set to draw the desktop
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

---

