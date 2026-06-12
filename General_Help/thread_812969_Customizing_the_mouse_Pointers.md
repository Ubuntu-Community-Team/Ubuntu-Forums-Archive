---
title: "Customizing the mouse: Pointers"
date: 2008-05-30
forum: General Help
---

### Post by Juleshu on 2008-05-30
Anyone know how to change the mouse pointer? Specifically I want to make mine larger, or change the arrow icon to something different like you can do in windows (ugh, I even hate typing it). I'm using hardy heron 64bit. Thanks!

---

### Post by NilsE on 2008-05-30
You can change mouse pointer themes in 

System > Preferences > Appearance > Customize 

and select from the default pointers.

You can also go to the following site and install more

[http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=20be88b1a888f4887785bac8d4b178bb](http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=20be88b1a888f4887785bac8d4b178bb)

---

### Post by Malvolio on 2008-05-30
While yes, there are alot of options for customizing the mouse, I think they were wondering about whether Ubuntu can be made as flexible as Windows in regard to customizing the mouse.  I know I miss my chocobo pointer that I made myself from screenshots of PoL.

---

### Post by NilsE on 2008-05-30
I agree, it would be nice if you could select individual pointers from a GUI like windows instead of having to add and modify a complete pointer theme. I am not aware of any initiative to do that so I also went ahead and created my own theme using an existing theme as a base and providing my own images which are png files.

---

### Post by Juleshu on 2008-05-30
Thanks, I found some nice pointers. I've installed them and I like them, but when I mouse to the top of a menu, or my desktop, or the panel, I get the standard ubuntu pointer. When I mouse back over a window, i get the new one I installed. Weird. It switches just like that. Thought maybe someone would know what i can do to fix this, if not, no big deal. Maybe it's an issue with the pointer theme I downloaded.

---

### Post by NilsE on 2008-05-30
> **Juleshu said:**
> Thanks, I found some nice pointers. I've installed them and I like them, but when I mouse to the top of a menu, or my desktop, or the panel, I get the standard ubuntu pointer. When I mouse back over a window, i get the new one I installed. Weird. It switches just like that. Thought maybe someone would know what i can do to fix this, if not, no big deal. Maybe it's an issue with the pointer theme I downloaded.
What that means is that that particular pointer is not in the new theme and when it uses that pointer it defaults to the gnome pointer. About the only way to fix that is find a theme that supports all pointers or add the pointer yourself.

If you have a theme with the source png files in it you may be able to figure out how to add one by duplicating the definition file, the png file, and add it to the script.

---

### Post by pmaconi on 2008-05-30
That isn't quite true. To apply your mouse theme to everything on your desktop, run the following code:```
gedit ~/.Xdefaults
```
Then add:```
Xcursor.theme: DMZ-Black
```
But replace DMZ-Black with whatever the name of your theme is. 

If you also want to change the GDM (login screen) mouse theme, run the following code:```
sudo gedit /usr/share/icons/default/index.theme
```

And add or modify:```
[Icon Theme]
Inherits=DMZ-Black
```
Replace DMZ-Black with whatever mouse theme you want (this may require something else for custom themes, I only changed mine to a different pre-installed one).

---

### Post by NilsE on 2008-05-30
Thats correct.  The Inherits=xxxxxxx is what causes a theme to use pointers from other themes when the selected theme does not include all pointers

---

