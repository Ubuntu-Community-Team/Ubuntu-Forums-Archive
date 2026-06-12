---
title: "Lubuntu Conky"
date: 2016-03-11
forum: General Help
---

### Post by jbcooper on 2016-03-11
Hello, I had a .conkyrc file that worked well in Lubuntu 15.04 but for some reason conky disappears in 15.10 and my efforts to stop it doing so by googling and tweaking the commands have not been successful. Any help at all, much appreciated.

---

### Post by Le3eVolfoni on 2016-03-11
Open the** .conkyrc** file and double save it to force it to (re)start. If it appears the it means the problem comes from the auto start. Otherwise change the value of **gap_x** (which is the horizontal position of your conky) cause maybe your conky is on but simply out of the screen. You can as well change the **own_window_type** (to **dock** for exemple) and then try to use the **gap_x** again. If nothing works copy/paste your** .conkyrc **file here so I can try it on my laptop.

---

### Post by ajgreeny on 2016-03-11
Does conky start at bootup, or at least with session start by adding it to the autostart list?

If so you will probably need to allow for a pause of 20 seconds (or thereabouts) to ensure the DE is fully running.  Use start command ```
conky -p 20
``` to do this.

As Le3eVolfoni says, it will be very helpful to see your ~/.conkyrc file, or whatever file you use for the configuration of conky.

---

### Post by jbcooper on 2016-03-11
The *-p 20* has solved it completely - thank you very much. I tried various **own_window_type** commands including *background*, *desktop* and *dock*, but they each have their own issues. However setting it to *background* with the *-p 20*, everything works absolutely great.

---

