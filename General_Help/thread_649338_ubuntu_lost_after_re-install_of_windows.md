---
title: "ubuntu lost after re-install of windows"
date: 2007-12-24
forum: General Help
---

### Post by jonascarter on 2007-12-24
Hi,

I recently had to re-install windows due to some bugs and such, and was given the option to choose which partition to install to, i chose the correct one (the one with windows on it to begin with) and did the whole setup again (as if new).

once setup was done, the ubuntu partition reads as empty. void of all information.

my boot up doesnt give me the option of ubuntu or windows xp anymore, it auto boots into windows. computer management in windows shows the partitons as empty and unused. did windows delete all my ubuntu stuff, or can i recover somehow? finding out i lost 250gb of usefull data and work files is not a good thing.

---

### Post by t-bone510 on 2007-12-24
Reinstall GRUB.

What happened was Windows overwrote the MBR, causing the GRUB bootloader to be replaced with the windows one.


You can reinstall GRUB with the ubuntu Live CD, heres some instructions. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by dlegend on 2007-12-24
I believe t-bone510 is right on (for your solution) -- I think Windows can't detect the linux filesystem so it appears to be empty and your GRUB loader got replaced. I don't think you actually lost all your data.

---

### Post by jonascarter on 2007-12-25
Thanks guys! i got my menu back.. however now when i choose any ubuntu version (even recovery), i get error 15 - file not found.

seems i did lose all the data.. CURSE MICROCRAP

thanks though!

---

