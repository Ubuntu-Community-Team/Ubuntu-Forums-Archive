---
title: "inkscape 0.46 affected by compiz-window-decorator plugin"
date: 2008-05-24
forum: General Help
---

### Post by realthor on 2008-05-24
Hy, I am using ubuntu 8.04 and was wondering if anyone noticed that inkscape 0.46 (from the repos), when maximized, flickers at each click on a tool. It is pretty annoying and after a few minutes playing with compiz i got to the compiz-window-decorator. The only way of making it stop is either stop the compiz-decorator plug-in which would make all windows without titles and stuff or make Inkscape full screen .

Any of you know a workaroud ?

Thanks.

---

### Post by realthor on 2008-11-11
long time no answer but now with intrepid ibex the same happens with blender (both windowed and full screen). While rotating view, clicking around, the window flickers and I can see the background, other windows etc through portions of the screen, a real mess.

Anyone with the same issue on blender+compiz?

---

### Post by Yashiro on 2008-11-11
Both systems cannot take control of the accelerated rendering space.
Just disable Compiz until Xorg and Video drivers catch up.

---

