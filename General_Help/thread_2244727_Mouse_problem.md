---
title: "Mouse problem"
date: 2014-09-18
forum: General Help
---

### Post by Chris_Shoup on 2014-09-18
So I was going to install Blender, but realized I didn't need to as my friend is going to be doing the modeling not me. Anyway, I typed this in to the console:
" gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier 'none' "
Now everytime I want to use my mouse it's all messed up. I have to press either ctrl or alt to make the mouse buttons work and it still wont work like a normal mouse. Please does anyone know how to fix this probelm? Easily?

---

### Post by Chris_Shoup on 2014-09-18
Still have this problem. I was just trying to follow a tut on blender but since i typed that in i have to hold ctrl or alt to use my mouse. If i just click on a window without pressing them buttons it moves the window.

---

### Post by Chris_Shoup on 2014-09-18
If anyone has this problem. You can fix it by just simply doing.
" gsettings reset org.gnome.desktop.wm.preferences mouse-button-modifier "

---

### Post by jamesshawver1 on 2015-04-01
gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier "<Super>"

Is the command that I originally used in order to fix the mouse problem and still be able to use Blender's alt + mouse button option.

---

