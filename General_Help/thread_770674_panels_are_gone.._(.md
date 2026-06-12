---
title: "panels are gone.. :("
date: 2008-04-27
forum: General Help
---

### Post by tubunu on 2008-04-27
Today after logging in I discovered the top and bottom panels are gone. I cannot access any programs (not even Terminal) because I don't keep shortcuts on the desktop. Alt + F2 doesn't work either. I logged in to fluxbox to type this. Hardy Heron seems to be giving me problems.. :confused:

---

### Post by wastedfluid on 2008-04-27
Have you tried booting into Recovery mode, and "startx" to test Gnome from there?  It might just be something in your gnome settings was corrupted... that'll be able to tell you.  Worse case worse, you can just wipe your settings.

---

### Post by tubunu on 2008-04-27
I'm sorry but I just can't seem to be able to do it. How do I wipe the settings? Isn't there an easier way to get back the panels? Come on.. it's not like I'm asking for something big.

---

### Post by tubunu on 2008-04-27
OK what I did was
```
sudo apt-get install gnome-panel
```
and they appeared. However, I do not understand why they disappeared in the first place. I don't remember uninstalling anything from my last boot. :confused:


BUT Trash and Volume icons are missing and if I add them manually I get this error: 
```
"The panel encountered a problem while loading: OAFIID:GNOME_MixerApplet". 
Do you want to delete the applet from your configuration?
[Don't delete] [Delete] 
```

and 

```
"The panel encountered a problem while loading: OAFIID:GNOME_Panel_TrashApplet".
Do you want to delete the applet from your configuration?
[Don't delete] [Delete] 
```

Please help. Thanks.

---

### Post by tubunu on 2008-04-27
In a HELP YOURSELF thread here's what I did that solved my problem: 

```
sudo apt-get install gnome-applets

```

---

### Post by Bubba64 on 2008-04-27
Right click in panel areas and hit add panels then right click in panel and then add to; everything in the basic set up is in add to menus etc. you can drag and drop other things you want like the browser etc. Sorry it looks like you got it figured out.

---

