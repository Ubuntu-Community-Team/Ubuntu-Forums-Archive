---
title: "My cube desktops feature is gone"
date: 2007-05-28
forum: General Help
---

### Post by sirab on 2007-05-28
I dont know what happened. I went to synaptics to download cinelerra and i downloaded a few other things...

and now my cube desktops feature is gone and i dont know what to do.

---

### Post by DcThePurger on 2007-05-28
enable it again?

---

### Post by sirab on 2007-05-28
its already enabled.. the wobbly windows thing is till working

is there a way to do it in terminal or something

---

### Post by CocoAUS on 2007-05-28
Are you using Beryl?  If so, right-click on the red Beryl gem in the task tray and select Beryl Settings Manager.  In the Desktop section, make sure Desktop Cube and Rotate Cube are enabled.  Having wobbly windows doesn't mean everything else is enabled.

If you're using Compiz, then try using gconf-editor to go through the settings and see if it got disabled somehow.

---

### Post by sirab on 2007-05-28
I'm using feisty fawn.

I'm such an idiot.

---

### Post by loathsome on 2007-05-28
This is a **known bug**!

I would recommend you to use the gnome interface instead ;) Grab the «gnome-compiz-manager» package! Eventually you COULD workaround the bug by typing the following in bash:```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

Good luck.

---

### Post by loathsome on 2007-05-28
Whops, forgot to mention. If you get the gnome interface, launch it by typing **gnome-compiz-preferences!** (or from the "System" menu)

---

### Post by godd4242 on 2007-05-28
> **sirab said:**
> I'm using feisty fawn.

I'm such an idiot.

Jeez buddy calm down.

---

### Post by sirab on 2007-05-28
Where would I get gnome-compiz-manager

---

### Post by CocoAUS on 2007-05-28
> **sirab said:**
> Where would I get gnome-compiz-manager

In Synaptic.  Or, you could use Terminal, and type
```
sudo aptitude install gnome-compiz-manager
```

It really doesn't matter.  You could also just copy and paste the commands he showed you and get the EXACT SAME effect.

---

### Post by sirab on 2007-05-28
> Jeez buddy calm down.

Sorry lol I'm so frustrated I just got done fixing all my other bugs.

---

### Post by sirab on 2007-05-28
Oh sweet it worked.

Thanks for all of your help.

---

### Post by loathsome on 2007-05-29
What worked? :) My workaround, or simply using the gnome-compiz thing?

Glad I could help!

---

### Post by bertlacy on 2007-06-10
> **loathsome said:**
> This is a **known bug**!

I would recommend you to use the gnome interface instead ;) Grab the «gnome-compiz-manager» package! Eventually you COULD workaround the bug by typing the following in bash:```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

Good luck.


I had the same problem and this fixed it!!!  Thx for the help!

---

