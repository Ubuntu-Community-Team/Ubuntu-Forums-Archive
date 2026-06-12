---
title: "How to add Main Menu in Cairo Dock"
date: 2008-06-07
forum: General Help
---

### Post by bmwman on 2008-06-07
How to add Main Menu in Cairo Dock? Is there a separate plugin or applet that needs to be installed? Also can I add the multiple deskpace icon? 

Thanks

---

### Post by Shazaam on 2008-06-07
As far as I know there is "no" main menu available for cairo-dock at the moment. The work-around that I found is to set up cairo-dock the way you like it. Make sure you set cairo-dock to load at boot by going to Preferences>Sessions and add it. Then open ccsm and enable "Widget Layer". Add this to the "Behavior" tab...
```
name=gnome-panel
```
Clean everything but the "Applications-Places-System" (main menu) off of the panel (you only need to keep one panel). When and if you need access to main menu hit your F9 key and the hidden panel will pop up. Hit F9 again to hide it.
BTW, I have tried kiba-dock, gdesklets and others and cairo-dock worked the best for me. YMMV!
Also, just drag the icons for apps you want to the dock to add them. It is also easy to make a sub-dock so you don't end up with a cluttered main dock.
I haven't added the workspace switcher to cairo-dock, I left that on the hidden gnome-panel. Cube rotate still works.

---

### Post by Genius314 on 2008-06-07
Apparently the latest version of Cairo-Dock (1.5.6) can use keyboard shortcuts. So you'd have to make a launcher that launches "<Alt>F1." Unfortunately, I couldn't get this to work...

---

### Post by Shazaam on 2008-06-07
> **Genius314 said:**
> Apparently the latest version of Cairo-Dock (1.5.6) can use keyboard shortcuts. So you'd have to make a launcher that launches "<Alt>F1." Unfortunately, I couldn't get this to work...

Yeah, that's what I ran up against and why I chose to use the ccsm method.

---

### Post by bmwman on 2008-06-08
> **Shazaam said:**
> As far as I know there is "no" main menu available for cairo-dock at the moment. The work-around that I found is to set up cairo-dock the way you like it. Make sure you set cairo-dock to load at boot by going to Preferences>Sessions and add it. Then open ccsm and enable "Widget Layer". Add this to the "Behavior" tab...
```
name=gnome-panel
```
Clean everything but the "Applications-Places-System" (main menu) off of the panel (you only need to keep one panel). When and if you need access to main menu hit your F9 key and the hidden panel will pop up. Hit F9 again to hide it.
BTW, I have tried kiba-dock, gdesklets and others and cairo-dock worked the best for me. YMMV!
Also, just drag the icons for apps you want to the dock to add them. It is also easy to make a sub-dock so you don't end up with a cluttered main dock.
I haven't added the workspace switcher to cairo-dock, I left that on the hidden gnome-panel. Cube rotate still works.


I already had that done. I really love the F9 feature with the widget layer. Anyway, i was trying see if there is a way to add the whole menu at once. I was creating few shortcuts and subdocks but that is very time consuming :)

BTW I was "cleaning" my orphaned packages and apparently "cleaned" more than I should and screwed up my whole system  :) Now I need a fresh install and redo all the tweaks I had done and reinstall everything :)I'll mess with cairo after that.

---

### Post by Forlong on 2008-06-08
If it's just the menu you need, you can create a new panel, un-expand it and only put the menu applet in there.
Then put it on any location you want on your desktop.

---

### Post by carrara47 on 2008-06-18
Hi,
I have done a script to load all the menu entries (applications and system) in the cairo dock.
See here
[http://ubuntuforums.org/showthread.php?p=5208447#post5208447](http://ubuntuforums.org/showthread.php?p=5208447#post5208447)

bye

---

### Post by El Viejo Lobo on 2009-02-23
I just strated Cairo and I found in one of the themes a "Main Menu" that worked out of the box, then I lost it somehow trying to add a nicer Icon but did remembered the comand line it add: [COLOR="Red"]**xdotool key "alt+F1"**[/COLOR]
I traid it on the terminal that answered that xdotool is not installed and if I whant it installed I have use the line:  [COLOR="Red"]**sudo apt-get install xdotool**[/COLOR] I installed it and made a new launcher that works all the time the original "Main menu " is kept in the upper panel, left side, where it comes when you first install Ubuntu.
I hope that you will enjoy it.

---

### Post by fabounet on 2009-02-23
the GMenu applet does the trick

---

