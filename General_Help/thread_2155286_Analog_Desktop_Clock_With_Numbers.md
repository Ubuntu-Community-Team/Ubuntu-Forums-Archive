---
title: "Analog Desktop Clock With Numbers"
date: 2013-06-17
forum: General Help
---

### Post by radacheck on 2013-06-17
I am looking for a large analog desktop clock with numbers.  I don't like digital clocks or clocks without numbers.
Thanks

---

### Post by cincinnatus13 on 2013-06-17
What DE are you running? Unity, Gnome, KDE? Answer will be different for each unless you're gonna run Conky.

---

### Post by CatKiller on 2013-06-18
Personally, I use one of the clocks in Screenlets to achieve this. There are many themes available for it.

---

### Post by stinkeye on 2013-06-18
Use cairo-clock. 
[ATTACH=CONFIG]243940[/ATTACH]
```
sudo apt-get install cairo-clock
```

[SIZE=3]**or**[/SIZE]
conky
[ATTACH=CONFIG]243936[/ATTACH] [ATTACH=CONFIG]243938[/ATTACH] [ATTACH=CONFIG]243939[/ATTACH]
```
sudo apt-get install conky-all
```
Conky needs a config file to determine what to display.
Download [DivShare File - conky_tar.gz](http://www.divshare.com/download/24225108-e6f) and extract.(File is 2.1mb due to clock_face images.)
****Note** that you will need to ctrl+h in nautilus to see the extracted hidden folder **.conky**
Place the **.conky** folder in your home directory.
Run conky, in the terminal...
```
conky -c ~/.conky/analog_clock1/conkyrc
```

The **~/.conky/analog_clock1/theme** folder contains 69 different clock_faces
To change to a different clock....in the terminal, run...
```
gedit ~/.conky/analog_clock1/conkyrc
```
and edit the last line to a [COLOR="#FF0000"]corresponding image number[/COLOR]...
```
${image ~/.conky/analog_clock1/theme/clock_face[COLOR="#FF0000"]65[/COLOR].png -p -0,0 -s 220x220}
```
[ATTACH=CONFIG]243937[/ATTACH]

---

