---
title: "Is there an app that does this?"
date: 2006-11-27
forum: General Help
---

### Post by rioghal on 2006-11-27
Ok, I'm looking for an app that allows the user to create themes/skins that can sit off the side of the desktop (out of view) and slides onto the desktop when the mouse cursor reaches the edge of the desktop.

I had Object Desktop software when I used Windows and I am looking to build a set of menus that sits off the desktop but slides onto the desktop depending on where the mouse cursor is. My goal is a desktop with nothing on it but there would be a menu widget on the left side, system prefs/gauges at the bottom and other stuff on the top and right sides but these things don't show up until I put the mouse cursor at the appropriate lcation and then the widget slides onto the desktop.

I tried gdesklets but it seemed really buggy and I'm not sure if superkaramba can even do this.

What do you all recommend?
EDIT: I use the Window Maker window manager instead of gnome or kde so I'd like to be able to do build things without have to load gnome or kde libs if possible.

---

### Post by gjtoth on 2006-11-27
Right-click on any existing panel and click "add panel"  You can customize them with just about anything you want and any way you want.  It's all built-in.  For system stats on your desktop, use gkrellm.

---

### Post by rioghal on 2006-11-27
> **gjtoth said:**
> Right-click on any existing panel and click "add panel"  You can customize them with just about anything you want and any way you want.  It's all built-in.  For system stats on your desktop, use gkrellm.

That would mean going back to gnome, and I don't want to leave Window Maker. Window Maker is quite awesome and I'd like to be able to do this in WM, sorry for not specifying this when I posted the original. Besides that, I want to be able to build things that "slide out" onto the desktop when the mouse cursor is placed at the edge of the screen and gkrellm doesn't do that. See screenshot.

---

### Post by gjtoth on 2006-11-27
Not familiar with WM.  However, you can always make the panel autohide.

---

### Post by rioghal on 2006-11-28
> **gjtoth said:**
> Not familiar with WM.  However, you can always make the panel autohide.

The gnome panels are not skinnable.. well, you can use different themes for GTK2 but that isn't what I call themable/skinnable.

I found a nice little app called wmdrawer.. it's a menu-bar type of dockapp that extends when the mouse hovers over it and retracts when the mouse leaves it. It'll do for now :) If you're interested in this app, simply do:

sudo aptitude install wmdrawer

then

man wmdrawer

---

### Post by xopher on 2006-11-28
You could try Beryl with Bdock, it's not finished yet - but it's getting there ;) Bdock is only available on SVN still so this would mean you'd have to compile it yourself.

---

