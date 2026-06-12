---
title: "GTK is ugly"
date: 2005-10-17
forum: General Help
---

### Post by ameerirshad on 2005-10-17
I have Breezy installed, and all the sudden (that is, without me given explicit or aware "go-ahead") my GTK engine has changed in some ugly grey/brownish color. While I am positive that under hoary it matched more or less with the rest of my GNOME Desktop.

Is there anyway to reinstall or change the GTK look & feel? I have tried the new "Art Manager", but that only let me download these GTK2! I have now a whole bunch of them on my pc and am not aware what to do with them. In the meanwhile Synaptic, Gaim and some other programs all have the same ugly lay-out that doesn't make them very appealing!

---

### Post by jasay on 2005-10-17
Art manager, as you found out, is for only downloading new themes.  Use System>Preferences>Theme to actually change the theme.  Hitting the theme details button on the right gives you the opportunity to mix and match different parts of the themes (icons, window border, etc.) I believe "Human" is the default theme if you just want it back to how it used to be.

---

### Post by ameerirshad on 2005-10-18
[QUOTE=jasay]Use System>Preferences>Theme to actually change the theme.  Hitting the theme details button on the right gives you the opportunity to mix and match different parts of the themes (icons, window border, etc.) I believe "Human" is the default theme if you just want it back to how it used to be.[/QUOTE]

Thanks Jasay, I will try, I did this btw and changed my theme to a combination of 

Controls: Dogmastik
Window Border: Vignette
Icons: Humility

But I didn't knew this affected my GTK2? It did change my AbiWord and OpenOffice and Firefox, and did so neatly........ however, Synaptic and Gaim look retarded :rolleyes: 

But again, I will try something else....... default for example

---

### Post by Corvillus on 2005-10-18
Anything that requires root privileges will use /root/.themes and /root/.icons instead of ~/.themes and ~/.icons (where ~ is your home dir), so any custom themes you install won't be visible on root applications such as synaptic. The fix i did was
```
sudo ln -s  ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by Seth on 2005-10-18
**Thank you!** This works for KDE too, and makes everything look soooooo much nicer.

---

### Post by bjtuna on 2005-10-25
awesome! thanks!

---

