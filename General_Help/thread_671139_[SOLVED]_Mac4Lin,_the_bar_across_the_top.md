---
title: "[SOLVED] Mac4Lin, the bar across the top"
date: 2008-01-18
forum: General Help
---

### Post by patrickaupperle on 2008-01-18
The bar across the top does not have the apple symbol among other things in it, how do i fix this?

---

### Post by jeffus_il on 2008-01-18
What would you like to see in the top panel and why?

---

### Post by patrickaupperle on 2008-01-18
the apple symbol it the top left like in the mac4lin screenshots

---

### Post by patrickaupperle on 2008-01-18
Like this

---

### Post by patrickaupperle on 2008-01-18
bump, Can anyone help?

---

### Post by EXCiD3 on 2008-01-18
To change the logo:

```
sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp <location of new .png> /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel
```

The first line creates a backup of the original image. You then need to download a png of the Mac logo that you want and then insert that image's location into the second command. Third command will kill gnome so that it will be reloaded with the new image!

---

### Post by patrickaupperle on 2008-01-18
Thankyou, i think I will try it when I get home. I am posting from my PSP right now, lol.

---

