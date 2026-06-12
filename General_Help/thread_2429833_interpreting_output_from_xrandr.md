---
title: "interpreting output from xrandr"
date: 2019-10-23
forum: General Help
---

### Post by Skaperen on 2019-10-23
a google search provided a clue to a "--listmonitors" option for [COLOR=#0000cd][FONT=courier new]**xrandr**[/FONT][/COLOR] as a way to get display geometry more accurate than [COLOR=#0000cd][FONT=courier new]**xwininfo**[/FONT][/COLOR] does.  the option is not described in the man page.  the output is providing some extra info that i do not understand.  does anyone know what the numbers 382 and 215 mean?
```

lt2a/forums /home/forums 15> xrandr --listmonitors
Monitors: 1
 0: +*eDP-1 1920/382x1080/215+0+0  eDP-1
lt2a/forums /home/forums 16> 

```

---

### Post by Holger_Gehrke on 2019-10-24
Seems like the documentation is stuck back on 1.4 while the program is version 1.5 ... Running 'xrandr --help' shows not only '--listmonitors' but also '--setmonitor <name> {auto|<w>/<mmw>x<h>/<mmh>+<x>+<y>} {none|<output>,<output>,...}' (and a few other surprises). I think the numbers you're wondering about are the 'mmw' and 'mmh' from --setmonitor. The name given (and the fact that the numbers fit with that interpretation on my system) makes me think those are the physical size of the display in millimetre as available from EDID. 

Holger

Edit: Yes, it's size in millimetres. At least the [documentation in freedesktop.org git]("https://gitlab.freedesktop.org/xorg/app/xrandr/raw/master/man/xrandr.man") says so.

---

