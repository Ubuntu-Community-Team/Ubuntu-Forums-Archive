---
title: "Stop window's decorations from fading"
date: 2008-04-27
forum: General Help
---

### Post by gsiliceo on 2008-04-27
I want to stop my windows decorations from fading when they lost focus, its annoying, i being searching for the value in compiz for 2 hours and i finally give up, please tell me.
The title bar gets a 40% increase in transparency, whats the setting i have to disable?
I forgot to mention im running hardy, and gutsy didnt showed this problem or if it did i disable it(cant remember)

---

### Post by deeesseee on 2008-04-27
Seconding this question.

I don't believe it would be in Compiz though, since the Windows Decoration plugin only includes options for shadows.

---

### Post by PhoenixP3K on 2008-04-27
I asked a similar question before. In gusty the transparency was applyed only to the title bar. Now it affects the entire border of the window.

---

### Post by edwebdev on 2008-04-27
I'm not sure if this is what you're looking for, but, in Gutsy and Hardy, if you go to System > Preferences > Appearance and opt for no visual effects, the border and title bar won't become partially transparent when the window loses focus. Of course then you will lose all of the other eye candy, but at least it's a start.

---

### Post by gsiliceo on 2008-04-28
I want the rest of the eye candy i love it, i just find that annoying.

---

### Post by gsiliceo on 2008-04-28
Found the solution guys!
> gconf-editor
THen go to apps / gwd
Change the opacity there, and you can play with the rest of the values to get other effects. 
CHeers!

---

### Post by deeesseee on 2008-04-29
Just to clarify this for other users:

Alt-F2 or whatever you run program set as, type "gconf-editor" and Configuration Editor should come up. Then navigate to apps/gwd/ then click on the key called "metacity_theme_opacity" and change that value to 1. This worked for me.

All credit goes to gsiliceo, or whatever his original source may have been.

Thanks!

---

### Post by overcyn on 2008-07-01
holy crap tytytytytytyty. been trying to fix this forever

---

