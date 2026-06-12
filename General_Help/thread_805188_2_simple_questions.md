---
title: "2 simple questions"
date: 2008-05-23
forum: General Help
---

### Post by tstack77 on 2008-05-23
I want my desktop to be a lot like [THIS]("http://szerencsefia.webs.com/photos/LUX-0.6.7.png") one. I tried installing this exact same one but a few things were left out.

How do I set the drop-down menu's opacity? I tried searching through the compiz setting manager but couldn't find it.

and,

How do I set a background picture/design for my folders? I really like the one he's using, but he left it out of the package.

thanks

---

### Post by Forlong on 2008-05-23
> **tstack77 said:**
> How do I set the drop-down menu's opacity?
See [here]("http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074") under Transparency.
> **tstack77 said:**
> How do I set a background picture/design for my folders?
While in Nautilus go to *Edit &#8594; Backgrounds and Emblems*

---

### Post by hollerith on 2008-05-23
1.  Opacity setting on dropdown menu is configured as follows:

Open Advanced Desktop Effects Settings.
Goto General Options ->Opacity settings tab
In Window Opacities create rules 

type=dropdownmenu  | 50
type=popupmenu     | 50

make sure you have the regex and dbus plugins on.

2.  Gnome folder background
Start up gconf-editor using Alt-F2 or from a terminal.
Search for the keys /apps/nautilus/preferences/background_filename
Don't forget to set draw backgorund as instructed.

---

### Post by tstack77 on 2008-05-23
Thanks!

---

### Post by Exsecrabilus on 2008-05-23
> **tstack77 said:**
> I want my desktop to be a lot like [THIS]("http://szerencsefia.webs.com/photos/LUX-0.6.7.png") one. I tried installing this exact same one but a few things were left out.

How do I set the drop-down menu's opacity? I tried searching through the compiz setting manager but couldn't find it.

and,

How do I set a background picture/design for my folders? I really like the one he's using, but he left it out of the package.

thanks
What is that theme, BTW?

It looks really nice.

---

### Post by tstack77 on 2008-05-26
[http://ubuntu.hamdi.web.id/themes/lux-theme.html](http://ubuntu.hamdi.web.id/themes/lux-theme.html)

---

### Post by Exsecrabilus on 2008-05-27
> **tstack77 said:**
> [http://ubuntu.hamdi.web.id/themes/lux-theme.html](http://ubuntu.hamdi.web.id/themes/lux-theme.html)
It says:

[quote=http://ubuntu.hamdi.web.id/themes/lux-theme.html]Forbidden

You don't have permission to access /themes/lux-theme.html on this server.[/quote]

---

