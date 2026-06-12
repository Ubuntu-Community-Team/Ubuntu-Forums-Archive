---
title: "Wine/Menu problem"
date: 2007-08-08
forum: General Help
---

### Post by Goombie on 2007-08-08
I have the default menu bar on my desktop, which I'm using for - what else - launching applications and such. :) I also want to be able to launch wine applications from the menu bar. I looked in alacarte, and I saw an option for wine-programs, but when I click this option to show it, nothing happens. I click the little checkbox to show the item on my main menu, but it doesn't show up, and the checkbox doesn't changed to checked. Any ideas?

---

### Post by avik on 2007-08-08
First of all, do you all already have some windows applications installed?  If not, install some.

If it still doesn't show up, then it's simply because there are no shortcuts under the WINE menu.  For me, for example, only two of my programs showed up in that menu.  Whatever the case, just add them manually using New Item.

In the command box, use something to the effect of:

```
env WINEPREFIX="/home/<*username>*/.wine" wine "C:\Program Files\path\to\program.exe"
```

---

