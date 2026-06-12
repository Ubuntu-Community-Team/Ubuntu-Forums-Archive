---
title: "Disable screen blanking in tty1 - tty6?"
date: 2007-03-08
forum: General Help
---

### Post by gumpish on 2007-03-08
Does anyone know how to disable screen blanking in tty1 through tty6?

I have various process/network monitors running and need them to remain visible without requiring mouse/keyboard input every few minutes.

I tried various permutations of setvesablank but it didn't result in any change.

(I also tried disabling the GNOME screen saver just in case, but still no change.)

Just to be clear, I'm referring to tty1 through tty6 (the consoles you access by pressing crtl+alt+F1 through F6), NOT gnome-terminal or xterm.

Thanks.

---

### Post by dannyboy79 on 2007-03-08
this has to do with power management doesn't it? are you saying that your monitor goes black? if so, then go under system, admin, the display prefs and change it to power saving off I would think. other wise I am not sure what you mean.

---

### Post by cookfromfrozen on 2007-03-08
**setterm -blank 0** disables screen blanking, but I'm not sure if it's permanent.  If it isn't you could possibly use an rc script to disable screen blanking for the ttys on boot, perhaps something like this:

/etc/init.d/local:

```
#!/bin/bash
setterm -blank 0 > /dev/tty1
setterm -blank 0 > /dev/tty2
setterm -blank 0 > /dev/tty3
setterm -blank 0 > /dev/tty4
setterm -blank 0 > /dev/tty5
setterm -blank 0 > /dev/tty6
```

chmod a+x /etc/init.d/local
update-rc.d local defaults 80

Hope this helps.

---

