---
title: "Help installing new GTK(2?) themes and ENGINES"
date: 2008-04-27
forum: General Help
---

### Post by snobby500 on 2008-04-27
Hey

Ive been messin with gtk2 themes recently and have installed a few but have had a few probs:

1) Synaptic looks ugly as well as a few other things is there a simple fix for this?

2)Some themes i installed have transparency on parts like menu bar, but although the theme works, it doesn't have transparency, do i have to manually set this?

3)Ok this is my main thing, is there some package or deb. file or some line of code which i can install to install pretty much all the engines for gtk2 themes in one go so i dont have to install each one separately? And is there anything i should watch out for when installing more engines?

4) Does someone have a nice light looking theme preferably with some sort of blue in there that you can suggest (light as in light coloured)

thanks

---

### Post by FuturePilot on 2008-04-27
1. The reason Synaptic and all other applications that are launched with root privileges look ugly is because root can't use your locally installed themes. If you want to fix this try this
```
sudo ln -s /home/<USERNAME>/.themes /root/.themes
```

2. You probably need Compiz and possibly Emerald (depending on the theme) to get the transparency effects

3. A lot of the gtk2 engines are in the repositories. If you search in Synaptic for gtk2-engines you will find a ton. Just be aware of gtk-qt-engine. Last I checked, the gnome-appearance-properties hates that engine and will lock up if you have it installed. There are a few engines that aren't in the repos however. Most likely you can find a .deb on [http://www.gnome-look.org/]("http://www.gnome-look.org/")

---

### Post by snobby500 on 2008-04-28
Hey, your command worked wonders :D just out of interest what did you exactly do, copy my themes folder to themes under root? so if i install more themes where should i put them?

Also i have compiz-fusion with gutsy or whatever it comes with as standard, and i found a thing under general options under advanced desktop effects settings to opacify windows but im not wure what to call the menu bar so im not sure how to opacify :S

thanks a lot for help so far

---

### Post by diafanos on 2008-04-29
> **snobby500 said:**
> Hey, your command worked wonders :D just out of interest what did you exactly do, copy my themes folder to themes under root? so if i install more themes where should i put them?

no. it just creates a link from root to your theme folders. So you can continue installing themes in your theme folder (because of the link, root can "see" these themes, too).



> **snobby500 said:**
> Also i have compiz-fusion with gutsy or whatever it comes with as standard, and i found a thing under general options under advanced desktop effects settings to opacify windows but im not wure what to call the menu bar so im not sure how to opacify :S

thanks a lot for help so far

just type:```
(type=popupmenu) | (type=dropdownmenu) 
```
and set opacity, whatever you want (IMO around 80 is ok)

---

### Post by snobby500 on 2008-04-29
Brilliant 
great help
thanks to both of u :)

---

