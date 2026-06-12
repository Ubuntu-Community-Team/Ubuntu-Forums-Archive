---
title: "transparent menus"
date: 2006-12-25
forum: General Help
---

### Post by Coop on 2006-12-25
Hello.
I am using Ubuntu 6.10 (GNOME).
I have installed Beryl and it is working perfectly,but the menus are not transparent.
How do I make the menus transparent?Please reply.
Regards Coop

---

### Post by brt on 2006-12-25
hmm i just know that its done via the state plugin, you just have to add the right window-class/title/name and opacity value to the settings of the state plugin:

eg., if you add this at "Window Opacity":  p:gnome-panel:50

your panel and gnome-menu has 50% opacity.

instead of "p" (owning program) you may also use:

w = window type 
c = window class
n = class name
r = class role

---

### Post by Coop on 2006-12-25
Hello.
Brt thank you for your reply.
But I don't understand what to do.Can you please explain it more?
Regards Coop

---

### Post by brt on 2006-12-25
You have to open Beryl Settingsmanager, 
either via right-click on the beryl-icon or press <alt><F2> and enter: beryl-settings

Select the "state" Plugin also called **"Set Window Attribs by varios criteria"**

Right at "String Lists" in the first row click "add" and enter:

    p:gnome-panel:50

 instead of "<New Value>"

now your gnome-panel and menu has 50% opacity, 
instead of 50 enter your desired opacity level.

you may enter anything in the form of:

X:value:YY

where:

 - X = one of p, w, c, n, r, t  (t = window title)
 - value = your desired value 
 - YY = the opacity level in % so eg. 90 will be 90% opacity


this command entered in the terminal:
```
xwininfo -all
```

gives you a crosshair to choose a window, if you click it, you get some info which may help you guess the right "values". i fear you have to experiment a little, as i do not know the right values for the gnome-menu, but you can use it on almost any window.

another example: 

    w:Tooltip:80

makes all your Tooltips transparent :)

---

### Post by hanzomon4 on 2006-12-26
Make your beryl-setting look like this:[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=21676&stc=1&d=1167110712[/IMG]

---

### Post by DarkN00b on 2006-12-26
Hey, that's cool. I was wondering how to use the window attribs plugin. The 50% setting worked great for me. Thanks.

While we're at it can I ask a question? I use a program called XNview to do image manipulation (red eye removal, various effects, etc.) The problem is that with Beryl running most of the window and its contents are treated like they are an alpha channel and are transparent or mostly transparent. I tried ```
p:xnview:100
``` but that didn't help. any ideas?

---

### Post by ~LoKe on 2006-12-26
I believe it's case sensitive, so try XNview, Xnview, XNView, etc.  I know that in order to get gnome-panel transparent, you need to write DOCK.

---

### Post by catfishk on 2007-07-18
you can loose the tooltips (the ugly yellow ones) or make them transparent by creating a 

 w:Tooltip:0

 entry in the box below labeled Absolute Window Opacity.  got that from here:

 [http://www.ytcracker.com/2007/04/](http://www.ytcracker.com/2007/04/)
 
 excellent!

---

### Post by strabes on 2007-07-18
> **catfishk said:**
> you can loose the tooltips (the ugly yellow ones) or make them transparent by creating a 

 w:Tooltip:0

 entry in the box below labeled Absolute Window Opacity.  got that from here:

 [http://www.ytcracker.com/2007/04/](http://www.ytcracker.com/2007/04/)
 
 excellent!

You could also just disable them in gconf-editor :)

---

### Post by mcduck on 2007-07-19
> **strabes said:**
> You could also just disable them in gconf-editor :)

No you can't. There's only option for Gnome-panel to remove tooltips, and even that doesn't remove them from all applets and launchers in panels.. ;)

---

