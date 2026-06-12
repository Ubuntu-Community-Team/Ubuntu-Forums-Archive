---
title: "Window decoration not showed in beryl"
date: 2007-06-16
forum: General Help
---

### Post by hecato on 2007-06-16
Hi there people, havent followed a guide...

But I have installed correctly the NVIDIA drivers for my 8800 GTS, it work OK with Ogre and Cgtutorial, I have searched beryl with synaptic and installed it (I have cheked in synaptic preferences to handle reccommended packages as if they where dependencies.



Now I go to Menu Apps-> System tools ->Beryl and in the beryl icon  right click and reload window manager

But that dosent seem to show the window decorations!!!!

Soon I will post a capture of the screen showing the proble, apparently beryl effcts are loaded, bu no windows decoration, the dindow decorator selected and the only 1 in the list is gtk window decorator!!!

---

### Post by raul_ on 2007-06-16
I'm not sure about this but here it goes:

type these commands 

```


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup


```

That creates a backup of your xorg configuration file.

now:

```
 gksudo gedit /etc/x11/xorg.conf
```

scroll down until you find "screen depth" and it should say 24. If it does, try changing it to 16, and then restart x (ctrl+alt+backspace) IF THIS BREAKS YOUR X SERVER DON'T BE SCARED AND READ ON

if you get your X borked, you'll get thrown into a terminal, so type this

```


sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf


```

to restore your previous (working) configuration. After this, to avoid problems, restart your computer

---

### Post by hecato on 2007-06-16
I will try what you suguest only I put the link to the capture [http://video.tleyotlocelocoatl.googlepages.com/noberyldecortion.avi](http://video.tleyotlocelocoatl.googlepages.com/noberyldecortion.avi)

Also I havent installed emerald that is why "gtk window decorator" I guess that is why was the only one listed in decorators.

---

### Post by hecato on 2007-06-16
I have checked what you say, asnt breaked the X  but hasnt any impact...

Also the only difference is that I now have emerald apart of gtk window decorator, but that also dosent impact in the decorations of beryl

---

### Post by raul_ on 2007-06-16
I'm out of solutions then. Try searching the Beryl forums, they should be much more qualified to answer this type of questions

---

### Post by Rui Pais on 2007-06-16
Hi,
try add the following line to Section "Device" of xorg.conf, under the line
Driver         "nvidia":
```
Option      "AddARGBGLXVisuals" "True"	
```
then restart X.

hth

---

### Post by hecato on 2007-06-16
I added the line without result.


I will try in the beryl forum... ammm [http://forum.beryl-project.org/](http://forum.beryl-project.org/) this one???

---

### Post by Depressed Man on 2007-06-16
Yes, that's the Beryl forum.

---

### Post by hecato on 2007-06-16
I havent needed to ask, running the commands at [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#An_automatic_easy_solution_for_.28almost.29_all_problems](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#An_automatic_easy_solution_for_.28almost.29_all_problems) solved the problem

---

### Post by orb9220 on 2007-06-16
Lately I also found if everthing is done right and still no beryl then go to extra's and disable the benchmark plugin. This happen at a couple of updates ago. And beryl will not work with this plugin enabled. Broken I quess.

---

### Post by hecato on 2007-06-16
Does any1 know if is posible to select metacity with a combination of keys???, something like CTRL}ALT}SUPR but for select metacity????

---

