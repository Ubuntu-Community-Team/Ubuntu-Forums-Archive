---
title: "Ubuntu 14.04 Gnome Flashback Compiz - how to disable panel launcher animations?"
date: 2014-08-14
forum: General Help
---

### Post by Rev2010 on 2014-08-14
I've switched from Metacity to Compiz since things such as resizing Windows in Metacity were terribly jerky and slow. Under Compiz it's super fluid. However, when I click the icons I added to the panel such as terminal, text editor, etc, they open with a quick animation. Not too big a deal, but I'd really like to disable them. I've tried the CompizConfig Settings Manager and turned off effects and tried various other settings but they persist. I also had the annoying issue of moving a window to the corners of the screen only to have them maximize every time, but I searched and found the info to disable that - boy was that annoying. Can anyone lend any info how to turn off 100% of Compiz effects and animations? In older Ubuntu versions this was under Appeance I believe, but alas for some reason some dev thought it brilliant to remove yet another easily adjustable option. 


Rev.

---

### Post by CantankRus on 2014-08-15
In terminal
```
gsettings set org.gnome.desktop.interface enable-animations false
```

You can also set metacity to use less resources...eg use wire frames when window resizing.
```
gsettings set org.gnome.metacity reduced-resources true
```

You will find these settings in **dconf-editor**
```
sudo apt-get install dconf-editor 
```

---

### Post by Rev2010 on 2014-08-15
Thanks so much CantankRus!! Worked like a charm.


Rev.

---

