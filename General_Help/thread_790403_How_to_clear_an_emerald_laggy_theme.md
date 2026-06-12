---
title: "How to clear an emerald laggy theme"
date: 2008-05-11
forum: General Help
---

### Post by hurinth on 2008-05-11
Hello. Yesterday I downloaded this theme > 80614-Q-Style.emerald and from Emerald themer I imported and began using it.

Everything was very cool till I realized the windows were too much laggy than before. I mean for example when u open a window from the Places menu, you see that window frame has the effect like being reduce in size until all the components appear and you're able to use the window. With the new theme I feel those effects are too much laggy.

So, I cleared the theme from Emerald>Themes Settings>Themes tab (I clic it and hit delete) But still the theme is here!

I would like to see my default gnome theme and check if it is as laggy as this theme.

Please advice

---

### Post by mano cazalet on 2008-05-11
you can install fusion-icon to switch between window managers (compiz/metacity) and window decorators (emerald/gtk)

---

### Post by hurinth on 2008-05-11
Mano I don't get what you are talking about, could you please say it with more details please ?

---

### Post by mano cazalet on 2008-05-11
so here it goes:

```
sudo apt-get install fusion-icon
```

this will install fusion-icon placing Compiz FusionIcon in Applications - System Tools

launch it and use it to switch between window decorators to see the difference and lagginess

---

### Post by hurinth on 2008-05-11
Can't get that icon, I no what ur talking about now, its the blue-white-arrow icon, but look > hurin@ASFALOTH:~$ sudo apt-get install fusion-icon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fusion-icon
hurin@ASFALOTH:~$ 


---

### Post by mano cazalet on 2008-05-11
hmm

just make sure
pls check if in System - Administration - Software Sources you have enabled the universe and multiverse repositories. If not enable them and reload. You should be able to install the fusion icon then

---

### Post by hurinth on 2008-05-11
No luck man... I hate when simple things get worst than they should

---

### Post by mano cazalet on 2008-05-11
:confused:

maybe if you try an other server and do a 
sudo apt-get update

edit: attached the deb i found in my cache
hope that helps you

---

### Post by Baltuki on 2008-05-12
hurinth, try this:

open System/Preferences/Advanced Desktop Effects Settings, then go to window decoration and write in the command line: > /usr/bin/compiz-decorator

---

### Post by hurinth on 2008-05-15
Fortunately I found [[COLOR="YellowGreen"]this great post[/COLOR]](http://ubuntuforums.org/showthread.php?t=792207&highlight=emerald+themes) and now everything is working

---

