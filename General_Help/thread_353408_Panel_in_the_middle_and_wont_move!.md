---
title: "Panel in the middle and wont move!"
date: 2007-02-04
forum: General Help
---

### Post by anaconda on 2007-02-04
Help!

I resized my screen to 800x600, and when I changed it back the gnome-panel stays in the middle of the screen.

rightclicking on the panel or trying to move it wont do any good. Cant' even remove any items from the panel, and cant get to panel properties.  

rebooting or "killall gnome-panel" dont have any effect. The panels are still in the middle of my screen.

EDIT: In this machine I have ubuntu 6.06

---

### Post by moshuptrail on 2007-02-04
A few questions:
1. The botttom panel?  Is the top panel working?
2. How do you know it's the panel and not a "picture" of the panel?
3. When you right click on it, what menu choices are displayed?

---

### Post by anaconda on 2007-02-04
Thanks for answering.
1. I dont have a top panel
3. And when I right clicked on the panel the only choises were. Help, and About Panels.. 
nothing else..

But just got it fixed :D  after 2 hours....
the problem was that I had apps/panel/global/locked_down selected from:
Applications > System Tools > Configuration Editor, 

Didn't remember that I had locked my panels to not accept any changes.. and then resizing the screen did change them anyway and locking didn't allow me to change them back..

---

