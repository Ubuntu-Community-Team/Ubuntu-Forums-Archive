---
title: "No sound when using Lubuntu on desktop computer"
date: 2015-02-03
forum: General Help
---

### Post by KayeNg on 2015-02-03
[COLOR=#000000][FONT=Helvetica Neue]Hi guys. [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Desktop computer has a dual boot system, Windows 7 and latest version of Lubuntu. [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Sound is OK when running Windows, but no sound in Lubuntu. [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]The PCI is: [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Intel 82801GB ICH7 - High Definition Audio Controller [A-1] [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Help please![/FONT][/COLOR]

---

### Post by sudodus on 2015-02-03
Try with PulseAudio and PavuControl

```
sudo apt-get install pulseaudio pavucontrol
```

Start ***PavuControl*** and work with all its menus to tweak the audio system. It may take time, but you will probably succeed :-)

---

### Post by KayeNg on 2015-02-05
Hey sudodus, thanks a lot, it did work! Took me about 3 to 4 minutes of tweaking.  I just wish it was this easy to install linksys ae2500 on my lubuntu desktop computer.  I always get errors when installing. Don't know if I should try again.

---

### Post by sudodus on 2015-02-05
You get better help with your wifi problem, if you start another thread with a good descriptive title. [COLOR=#696969]People helping to solve wifi problems will probably not read your thread about 'no sound'.[/COLOR]

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

