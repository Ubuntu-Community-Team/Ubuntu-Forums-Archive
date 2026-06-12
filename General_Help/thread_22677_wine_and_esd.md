---
title: "wine and esd"
date: 2005-03-29
forum: General Help
---

### Post by k84 on 2005-03-29
I installed crossover office just to get the plugins for wmp and qt work on firefox, the problem i have is that there's no sound at all but te video is fine. I looked into the config file of wine and I found that it is using oss driver instead of esd which is the one i use for my hoary box. is there a way i can get the wine driver for ESD??... by the way i know there is a mplayer plugin for mozilla but i really dont like cuz for quick time videos there's no slide control, and for wmp formats mplayer sometimes is not well recognized...

---

### Post by MrBrownstone3g on 2005-04-20
Currently Wine the program Crossover office is based upon doesn't support ESD(The program the controls sound in ubuntu) so you have have to shut ti down before you run your windows program, This is fairly simple to do:
[I]
Open a console window
type: killall esd
Run your windows program and you should have sound 
when your finshed remeber to restart ESD by typing esd at a console[/I]

Hope this is usefull!!

---

