---
title: "Please I need urgent help...I've screwed up my system"
date: 2014-07-29
forum: General Help
---

### Post by brickbat on 2014-07-29
Hi,

I installed and ran compiz manager to try to improve the usability of my system.  I adjusted the mouse settings so that I can add a mouse trail and I played with a couple of other settings.  The changes caused my screen to stop being responsive so I went into preferences and reset settings to default.  That totally killed my menu and dock thing on the left hand side.  I tried rebooting and it's still gone.  I cant run anything.  Pressing Alt or the super key does nothing.  OMG I can't believe restoring to default can do this!

Please help me fix it. I'm desperate.

---

### Post by Jesse_Campton on 2014-07-29
Ctrl+Alt+T to open a terminal, if terminal does not open try ctrl+alt+F1. Log in, Then try the following ```
[COLOR=#453E3E][FONT=arial]sudo apt-get install dconf-tools[/FONT][/COLOR]

``` ```
[COLOR=#453E3E][FONT=arial]dconf reset -f /org/compiz/[/FONT][/COLOR]
``` ```
[COLOR=#453E3E][FONT=arial]setsid unity[/FONT][/COLOR]
``` ```
[COLOR=#453E3E][FONT=arial]unity --reset-icons[/FONT][/COLOR]
```

---

### Post by brickbat on 2014-07-29
OMG THANKS!!!!!! Worked perfectly.

---

### Post by Jesse_Campton on 2014-07-29
Welcome, mark thread as solved.

---

