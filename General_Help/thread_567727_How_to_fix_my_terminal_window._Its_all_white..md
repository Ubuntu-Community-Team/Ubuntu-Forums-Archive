---
title: "How to fix my terminal window. Its all white."
date: 2007-10-04
forum: General Help
---

### Post by TheShadows on 2007-10-04
Hey how do i fix my terminal window because its all white? I did try this:

```
compiz --replace
```

Didn't fix my terminal window.

---

### Post by jwcgator on 2007-10-04
if you're running nvidia's proprietary drivers, type this into a terminal:
```
 sudo nvidia-xconfig --add-argb-glx-visuals
```

and restart. 

It fixed this problem for me.

---

### Post by TheShadows on 2007-10-04
Does it doe something after you type it in? Because i typed it in and restarted and nothing happened.

---

### Post by TheShadows on 2007-10-04
Anyone know how to fix?

---

### Post by TheShadows on 2007-10-05
bump

---

### Post by arekmenner on 2007-10-05
I don't know how to fix your problem, but if you tell people what graphics card you're running, what distribution of linux (feisty, edgy, gutsy), what desktop manager (gnome, kde), what terminal you're using, and whether or not you're using desktop effects (compiz or beryl) people may be able to better diagnose the problem.

Thanks for using ubuntu! :)

---

### Post by TheShadows on 2007-10-05
> **arekmenner said:**
> I don't know how to fix your problem, but if you tell people what graphics card you're running, what distribution of linux (feisty, edgy, gutsy), what desktop manager (gnome, kde), what terminal you're using, and whether or not you're using desktop effects (compiz or beryl) people may be able to better diagnose the problem.

Thanks for using ubuntu! :)

Graphics: Nvidia GForce 2 MX 400
Distro: Feisty
DM: Gnome
Terminal: What ever Ubuntu uses after install.
Desktop Effects: Compiz

Thats about all I can say about my Distro, i'm new to Ubuntu. Have used Linux before but not at my own home.

---

### Post by anaconda on 2007-10-05
maybe I understood wrong? but if it is otherwice working, eg. other programs work,  but the terminal is white, then you can change terminal:s colour (and text colour if it is also white)  from "Edit>current profile>colours" from terminals menu..

or you could install eg. xterm, which is just another terminal program.

---

### Post by TheShadows on 2007-10-05
It was working, but the whole box even border and menus are completely white. Now I can click on the Menu's and when they pop up they show up. I've tried changing the colors in the Profile for the Terminal but that doesn't seem to have any effect on it at all.

A guy I work with uses it and he suggest turning off Desktop Effects to see if that made a difference. But I haven't tried that yet since i'm at work. 

Is Xterm in the Synaptic Package Managers?

---

### Post by anaconda on 2007-10-05
> **TheShadows said:**
> 
Is Xterm in the Synaptic Package Managers?

Yes it is. other ones you might want to try are konsole and tilda. (konsole is KDE:s terminal)

---

### Post by philinux on 2007-10-05
It might be an installed desktop theme your using i had this with firefox having white fonts on a white backgroung. Had to get rid and try another theme.

---

