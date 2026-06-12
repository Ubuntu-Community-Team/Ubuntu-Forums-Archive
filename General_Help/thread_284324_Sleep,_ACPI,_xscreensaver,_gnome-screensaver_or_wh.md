---
title: "Sleep, ACPI, xscreensaver, gnome-screensaver or what?"
date: 2006-10-25
forum: General Help
---

### Post by neymac on 2006-10-25
I have a desktop (with nVidia 5200) that the monitor blanks every 10 minutes I stop moving mouse or typpings. It is annoying because it occurs even with totem running, and I have to move the mouse every 10 minutes to return the screen.

I have tried everything I know to fix this:
gnome-screensaver settings
xscreensaver settings
gnome-power-manager

I changed the values and still remains the problem at exact 10 minutes the display blanks and comes back when I move the mouse or type something.

I using Dapper with XGL/Beryl at a XGL session.
I have searched for similar problems at this forum, but nothing.

Did anyone have this problem and got it fixed?
Does anyone know where I find a way to fix this?

The result of  xset -q is:

xset -q```

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfffef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  7/2    threshold:  5
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/lib/X11/fonts/misc/,/usr/lib/X11/fonts/Type1/,/usr/lib/X11/fonts/100dpi/,/usr/lib/X11/fonts/75dpi/
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Display is not capable of DPMS
```

---

### Post by neymac on 2006-10-25
I started a WindowMaker session at the same desktop and the blanking at every 10 minutes didn't.

---

### Post by aidanr on 2006-10-25
happened for me aswell, i ran gconf-editor as user and as root and went to the gnome-power-management entry(i think thats it, at work can't check) and unchecked "can suspend" i think that solved it

btw i also changed some other things in there such as "can hibernate" so i'm not sure which option fixed it

---

### Post by neymac on 2006-10-25
I unchecked both can hibernate and suspend as user and sudo  but didn't work.
I'm running a XGL session.

---

### Post by viranaso on 2007-11-16
Do it the GUI way: choose menu items System, Preferences, Screensaver and you can change the delay etc.

---

