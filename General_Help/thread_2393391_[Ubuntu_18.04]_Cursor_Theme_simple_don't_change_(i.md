---
title: "[Ubuntu 18.04] Cursor Theme simple don't change (it works only for the GTK windows)"
date: 2018-06-02
forum: General Help
---

### Post by nooneelse on 2018-06-02
It's been a while since I am trying to change the theme of my cursor. Using gnome-tweak-tool I can change it, but it only changes in GTK windows, when I move the mouse to the X server area (desktop for example) it returns to a default one.

I am trying to install Capitaine, I already did (logout and restarted everytime):

sudo update-alternatives --config x-cursor-theme
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /home/bruno/.icons/Capitaine/index.theme  <--- ( and then repeated the previous command above to enable it)

Already created the "cursor.theme" file and added the "Inherits=Capitaine", also tried to add that parameter inside the "index.theme"...

Really I am out of options, if anybody could help me, I would appreciate.

Thanks in advance.

---

### Post by Dennis N on 2018-06-02
**index.theme** at end of your command should be **cursor.theme** and there should be a priority number added after that (20, for example)
Also, you may need to have the cursor folder in **/usr/share/icons**. I always put it there.

Sample of a correct install command:
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/Breeze-White/cursor.theme 20
```

---

