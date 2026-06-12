---
title: "shortcut overlay (arrow) emblem will not go away!"
date: 2013-09-05
forum: General Help
---

### Post by Donny Bahama on 2013-09-05
I've replaced every single emblem-symbolic-link  emblem on my computer with a blank/transparent image. I used gimp to  edit/overwrite all occurrences of emblem-symbolic-link.png, and inkscape  to edit/overwrite emblem-symbolic-link.svg - - and STILL, those blasted  arrows are sitting on top of my icons! I've gone back in to confirm that the emblems are, in fact, transparent. Are these emblems cached somehow/somewhere?

Has anyone else encountered this? Can anyone PLEASE suggest a solution?

---

### Post by stinkeye on 2013-09-05
When using the default ubuntu-mono-dark icons, links appear to use  /usr/share/icons/Humanity/emblems/...

Ran 
```
gksudo nautilus /usr/share/icons/Humanity/emblems
```
Searched for **emblem-symbolic-link** 

No need for gimp. Just appended any png or svg files with **.bak**
eg **emblem-symbolic-link.svg.bak**

Reloading in the file browser or resizing on the desktop, then showed the linked file without the arrow overlay.

---

### Post by Donny Bahama on 2013-09-05
Thanks for the help, stinkeye! I understand where the files are located, and I went ahead and renamed them...

```
 /usr/share/icons $ find -name 'emblem-symbolic*'
./HighContrast/scalable/emblems/emblem-symbolic-link.svg.bak
./gnome/8x8/emblems/emblem-symbolic-link.png.bak
./gnome/16x16/emblems/emblem-symbolic-link.png.bak
./gnome/48x48/emblems/emblem-symbolic-link.png.bak
./gnome/24x24/emblems/emblem-symbolic-link.png.bak
./gnome/22x22/emblems/emblem-symbolic-link.png.bak
./gnome/256x256/emblems/emblem-symbolic-link.png.bak
./gnome/32x32/emblems/emblem-symbolic-link.png.bak

```

Overlay emblems are still there! I can only assume that there must be an overlay emblem living somewhere outside of /usr/share/icons, but...

```
user-HP-Pavilion-g7-Notebook-PC / # find -name 'emblem-symbolic*'
./usr/share/icons/HighContrast/scalable/emblems/emblem-symbolic-link.svg.bak
./usr/share/icons/gnome/8x8/emblems/emblem-symbolic-link.png.bak
./usr/share/icons/gnome/16x16/emblems/emblem-symbolic-link.png.bak
./usr/share/icons/gnome/48x48/emblems/emblem-symbolic-link.png.bak
./usr/share/icons/gnome/24x24/emblems/emblem-symbolic-link.png.bak
./usr/share/icons/gnome/22x22/emblems/emblem-symbolic-link.png.bak
./usr/share/icons/gnome/256x256/emblems/emblem-symbolic-link.png.bak
./usr/share/icons/gnome/32x32/emblems/emblem-symbolic-link.png.bak
user-HP-Pavilion-g7-Notebook-PC / # 

```

:confused:

---

### Post by stinkeye on 2013-09-05
What I described above works for me with default icons but with other
icon sets I still get a link overlay (pic), even after renaming files.
Don't know where it's coming from???
The overlay being used is not in the theme I have chosen.
So yeah, I'm not much help really.

---

