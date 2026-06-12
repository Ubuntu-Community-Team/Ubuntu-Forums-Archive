---
title: "Opera using KDE colors in Gnome"
date: 2007-04-25
forum: General Help
---

### Post by m.musashi on 2007-04-25
I have been playing with Opera and I really like it. I was also playing with KDE once again but now I'm back in Gnome. Opera, however, continues to use the KDE colors and doesn't mesh with Gnome. I've tried reinstalling it and I've tried using skins but the menu bar continues to be the color I selected in KDE and will not use the GTK theme (in this case Onyx-red). See screen shots for clarification.

Does anyone know how to fix this?

Thanks.

---

### Post by zvacet on 2007-04-25
It looks like somrthing from KDE is left in system,and Opera continue to use that.But,that is just my opinion.

---

### Post by m.musashi on 2007-04-25
Thanks for the help but it's a moot issue now. I messed some other things up and ended up doing a reinstall. Now Opera looks fine - although KDE is not installed yet. I wonder what will happen if I install it???

EDIT: I lied. Menus and such are still using KDE themes. I think Opera is a KDE app (at least the package name has QT as part of it). If anyone knows how, I would still like to fix this.

Thanks.

---

### Post by Sladi on 2007-04-29
I have the same problem. How can I change the menu colours?

---

### Post by risidoro on 2007-04-30
It's quite simple to adjust opera and make it looks like a gnome app:

- Install qt3-qtconfig and polymer packages using synaptic

- From a shell, run qtconfig and adjust the fonts, the colors and the style (choose polymer as style)

- From a shell, run polymer-config and enable software tint transparency (if you like it)

- Choose an Opera skin that resemble a gtk app, i.e. tango_cl or qute



Have fun with the best browser ever made :)

---

### Post by Sladi on 2007-04-30
Thanks a lot risidoro! :biggrin: 


Regards, 
Sladi

---

### Post by m.musashi on 2007-04-30
Thanks. That got things pretty close. Too bad there isn't a gtk version of Opera. I think I'm going to have to fix it each time I change themes.

---

### Post by Sladi on 2007-05-03
When I type qtconfig I get this error: 
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Now the menu bar is always the same colour. Usually themes changed it. Also the background is wrong. Can I revert to what it was before (ie let the themes change the colours)? 
I noticed a new account on my PC doesn't have this problem. 
[[img]http://xs115.xs.to/xs115/07184/Screefgn.png[/img]](http://xs.to) [[img]http://xs115.xs.to/xs115/07184/page.png[/img]](http://xs.to)

---

### Post by pjalegria on 2007-06-15
I have the same problem, thats why I dont use Opera...:(

---

