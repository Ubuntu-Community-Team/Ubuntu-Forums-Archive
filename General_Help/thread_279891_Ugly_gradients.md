---
title: "Ugly gradients??"
date: 2006-10-18
forum: General Help
---

### Post by eggmanpete on 2006-10-18
I have installed the nvidia drivers and managed to play enemy territory, however, when the gnome shutdown menu (log off, switch user and all that) is clicked and everything fades out, it looks really ugly as and has a gradient between colours as if its not 24bit colours or somethin like that, anyone know what to do?

also: when i load a page in firefox, everything kind of tears and looks like the page has been put into a blender, maybe something to do with the above problem.

Im running dapper x64
Cheers, eggman

---

### Post by K.Mandla on 2006-10-18
Have you installed Beryl or XGL? I used to get freaky displays like that when I had XGL and had set the color depth wrong. If I remember correctly, your /etc/X11/xorg.conf file should have 24 for the color depth.

Just an idea.

---

### Post by eggmanpete on 2006-10-18
XGL isnt installed at the moment

xorg.conf reads:

Section "Screen"
          DefaultDepth         24

notice, no "" brackets like on any other attributes??

---

### Post by K.Mandla on 2006-10-18
No, no quotes on the DefaultDepth. Try knocking it down to 16 and see if the gradient effect goes away. I don't know for certain, but it might have something to do with video memory too. What resolution is your monitor? What kind of video card do you use?

---

