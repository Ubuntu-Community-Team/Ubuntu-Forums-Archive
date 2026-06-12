---
title: "That little icon in the upper corner of Windows"
date: 2006-10-08
forum: General Help
---

### Post by GStubbs43 on 2006-10-08
Hi all, I'm not sure exactly where to put this thread, so I'll ask here. ;)
You know that icon in the upper left hand corner of all windows? Is it possible to change that? Specifically in Iceweasel (see attached image) Thanks! :-D

---

### Post by fatsheep on 2006-10-08
I would like to know this as well.

---

### Post by CatKiller on 2006-10-08
If you mean the **left** corner, that's the menu button. You can move or remove it by opening **gconf-editor** and editing the "button_layout" key at apps/metacity/general.

---

### Post by GStubbs43 on 2006-10-08
> **CatKiller said:**
> If you mean the **left** corner, that's the menu button. You can move or remove it by opening **gconf-editor** and editing the "button_layout" key at apps/metacity/general.


oh man! haha, Yeah, I meant *left* 
But I don't want to move/remove it, I want to change it. I guess my question was a bit confusing. ;)

---

### Post by fatsheep on 2006-10-09
Anyone?

---

### Post by CatKiller on 2006-10-09
> **fatsheep said:**
> Anyone?

> You can move or remove it by opening gconf-editor and editing the "button_layout" key at apps/metacity/general.:KS

---

### Post by fatsheep on 2006-10-09
> **CatKiller said:**
> :KS

> Arrangement of buttons on the titlebar. The value should be a string, such as "menu:minimize,maximize,close"; the colon separates the left corner of the window from the right corner, and the button names are comma-separated. Duplicate buttons are not allowed. Unknown button names are silently ignored so that buttons can be added in future metacity versions without breaking older versions. 

We are trying to add an icon for iceweasel that will appear in the top left corner of the window.  We are not trying to make a global change to the titlebar.

---

### Post by CatKiller on 2006-10-09
> **fatsheep said:**
> We are trying to add an icon for iceweasel that will appear in the top left corner of the window.  We are not trying to make a global change to the titlebar.

Sorry, my mistake. I really should learn to read the question better when I'm tired. Of course, the fact that I'm on the Ubuntu forum in the middle of the night probably doesn't help.

To answer your **actual** question then, is that lack of icon theme-independent - that is, do you get the default icon for iceweasel, regardless of the theme that you're using? I'm afraid I don't use it, so I can't check. If so, I believe the default icon can be changed by changing application-default-icon.png in /usr/share/icons

---

### Post by fatsheep on 2006-10-09
> **CatKiller said:**
> Sorry, my mistake. I really should learn to read the question better when I'm tired. Of course, the fact that I'm on the Ubuntu forum in the middle of the night probably doesn't help.

To answer your **actual** question then, is that lack of icon theme-independent - that is, do you get the default icon for iceweasel, regardless of the theme that you're using? I'm afraid I don't use it, so I can't check. If so, I believe the default icon can be changed by changing application-default-icon.png in /usr/share/icons

Yea I get this default icon for iceweasel no matter what.  However, changing the application-default-icon is not what I want to do either.  I would like to give iceweasel and iceweasel only the iceweasel icon.

---

### Post by CatKiller on 2006-10-09
[I see now]("http://en.wikipedia.org/wiki/Iceweasel") why Iceweasel may not have an icon of its own. I am somewhat out of my depth on this one, having not used Iceweasel, nor knowing much about themes. However, if you create an icon called iceweasel.png in /usr/share/pixmaps, say, and assign that to the Iceweasel launcher, does it automagically get transferred to the Window Menu Button? Or do you have that already?

---

### Post by GStubbs43 on 2006-10-09
Nope, that doesn't work, it used the icon while Iceweasel was loading in the window list in the panel, but then it just went back to how the screenshot in my first post looks. Any other ideas?

---

### Post by CatKiller on 2006-10-09
Not really. As I said, I don't know that much about how theming works. Possibly the icon needs to be part of the application in some way? Now I actually know what (and why) Iceweasel is, it seems possible that they haven't gotten round to putting their own branding in. Otherwise, I guess you could reseach (Metacity?) themes - it's all a bit over my head for 4 in the morning.

---

### Post by fatsheep on 2006-10-10
Well I don't see why they can't use the plain globe, that's not a firefox trademark...

---

### Post by GStubbs43 on 2006-10-14
Anyway... anyone know how to at least just make all the windows have the same icon, like the little oval here: [http://linuxplanet.com/graphics/screenshots/gnome_osx.png](http://linuxplanet.com/graphics/screenshots/gnome_osx.png)
?

---

### Post by fatsheep on 2006-10-14
Someone on the bug list just told me how to get the icon on the Iceweasel window so I thought I'd pass it a long... All you have to do is copy an image to /usr/local/Iceweasel32/chrome/icons/default/default.xpm. First off, create a directory named "icons" under the chrome folder. Then create a folder named "default" under icons. Now run this command:

sudo cp /usr/share/pixmaps/iceweasel32.png /usr/local/Iceweasel32/chrome/icons/default/default.xpm

Or just put any icon you like in there named as "default.xpm".

[img]http://img295.imageshack.us/img295/1302/iceweaseloj8.png[/img]

---

### Post by GStubbs43 on 2006-10-14
Awesome,thanks, I'll try that. :)

---

